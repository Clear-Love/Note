## 一、实验目的

1. 熟悉`Android`程序设计的基本概念；
2. 对比认识`SQL`与`SQLite`基本概念、实现方法；
3. 熟练掌握`SQLite`中数据操作方法；
4. 能够结合`SharePreferences`，完善实验一中的项目，实现数据操作的多种方式配合。

## 二、实验内容要求

1. 用`adb shell`创建数据库；
2. 用标准SQL语句操作`SQLite`；用`SQLiteDatabas`e的方法操作`SQLite`；拷贝数据库到`SD`卡上；
3. 进一步加深对数据库操作的理解认识，写出自己的心得体会。

详情：

1. 了解`adb shell`并能用命令实现数据库创建等操作；
2. 对比数据库原理，理解标准`SQL`语句操作`SQLite`的使用；
3. 掌握`SQLiteDatabase`操作`SQLite`的方法；实现数据库与`SD`卡的交互；
4. 对实验一项目，添加数据库操作功能，实现前后台的数据交互及可靠性操作响应

## 三、实验详细报告

### 电子书阅读器SQL的数据库结构：

电子书阅读器中数据库模块是项目中不可或缺的一部分，它提供了一个完整的电子书管理系统，可以方便地存储和管理电子书的基本信息、章节信息和章节内容信息。

数据库实体定义：

数据库使用了 Room（SQLite）作为本地数据存储和访问的解决方案，这是一种非常流行的 ORM（对象关系映射）库，可以帮助我们更轻松地管理应用程序中的数据。我设计了两个个实体类：Chapter 和 Book。Chapter 实体类用于存储电子书的章节信息和内容，Book 实体类用于存储电子书的基本信息，如标题、封面图片、描述等。两个表通过bookId进行关联，实现的一本图书有多个章节的一对多关系。

- BOOK字段及其定义

```kotlin
@Parcelize  
@Entity  
data class Book(  
	var isbn: String?, // ISBN编号  
	@PrimaryKey var bookId: Int,  // id，主键
	var title: String, // 书名  
	var author: String?, // 作者  
	var publisher: String?, // 出版社名称（外码）  
	var publishDate: String?, // 出版时间  
	var language: String?, // 语言  
	var collectCount: Int, // 收藏次数  
	var description: String?, // 简介  
	var price: String?, // 价格  
	var coverImage: String?, // 封面  
	var ratingNUm: String?, // 评分  
	var completed: Boolean = false, // 是否读完  
	var inLibrary: Boolean = false, //是否在书架  
	val lastReadEpochTimeMilli: Long = 0,  // 最后阅读时间
) : Parcelable@Parcelize
```

- Chapter字段及其定义

```kotlin
@Entity  
data class Chapter (  
	val title: String,  // 章节标题
	@PrimaryKey val url: String,  // 章节url
	val bookId: Int,  // bookID 外键约束
	val position: Int,  // 章节位置
	val read: Boolean = false,  // 是否阅读
	val lastReadPosition: Int = 0, // 最后阅读位置  
	val lastReadOffset: Int = 0, // 最后阅读偏移值  
	val body: String //章节内容  
)
```

- 数据库定义

定义了两个Dao类，实现对图书及其章节的操作，如：查询某本书的所有章节、更新章节信息、将章节标记为已读，查询某本书的第一章节、更新章节标题、将章节标记为未读。

```kotlin
@Database(entities = [Book::class, Chapter::class], version = 2)
abstract class AppDatabase : RoomDatabase(){
    abstract fun bookDao(): BookDao
    abstract fun chapterDao(): ChapterDao

    companion object {
        private const val DATABASE_NAME = "Lib"
        // 从数据库文件创建实例
        fun createRoom(ctx: Context) = Room
            .databaseBuilder(ctx, AppDatabase::class.java, DATABASE_NAME)
            .addMigrations(*migrations())
            .build()

        // 从输入流创建实例
        fun createRoomFromStream(ctx: Context, inputStream: InputStream) = Room
            .databaseBuilder(ctx, AppDatabase::class.java, DATABASE_NAME)
            .addMigrations(*migrations())
            .createFromInputStream { inputStream }
            .build()

        private fun migrations(): Array<out Migration> {
            return arrayOf(
                object : Migration(1, 2) {
                    override fun migrate(database: SupportSQLiteDatabase) {
                        // 更新数据库架构
                    }
                }
            )
        }
    }
}
```

- BookDao

```kotlin
@Dao
interface BookDao {
    @Query("SELECT * FROM Book")
    suspend fun getAll(): List<Book>

    @Insert(onConflict = OnConflictStrategy.IGNORE)
    suspend fun insert(book: Book)

    @Insert(onConflict = OnConflictStrategy.IGNORE)
    suspend fun insert(book: List<Book>)

    @Query("SELECT * FROM Book WHERE bookId = :id")
    suspend fun getById(id: Int): Book?

    @Query("SELECT * FROM Book WHERE inLibrary == 1")
    suspend fun getAllInLibrary(): List<Book>

    @Query("SELECT * FROM Book WHERE inLibrary == 1")
    fun booksInLibraryFlow(): Flow<List<Book>>

    @Update
    suspend fun update(book: Book)

    @Delete
    suspend fun delete(book: Book)

    // 查询某本书的所有章节
    @Query("SELECT * FROM chapter WHERE bookId = :bookId")
    suspend fun getChaptersByBookId(bookId: Int): List<Chapter?>?

    // 查询所有章节
    @Query("SELECT * FROM chapter")
    suspend fun getAllChapters(): List<Chapter?>?

    // 查询所有书籍，按最后阅读时间逆序
    @Query("SELECT * FROM book ORDER BY lastReadEpochTimeMilli DESC")
    suspend fun getAllBooksByLastReadTime(): List<Book>

    @Query("SELECT EXISTS(SELECT * FROM Book WHERE bookId == :bookId AND inLibrary == 1)")
    suspend fun existInLibrary(bookId: Int): Boolean

    // 查询
    @Query(
        """
        SELECT Book.*, COUNT(Chapter.read) AS chaptersCount, SUM(Chapter.read) AS chaptersReadCount
        FROM Book
        LEFT JOIN Chapter ON Chapter.bookId = Book.bookId
        WHERE Book.inLibrary == 1
        GROUP BY Book.bookId
    """
    )
    fun getBooksInLibraryWithContextFlow(): Flow<List<BookWithContext>>
}
```

- ChapterDao

```kotlin
@Dao
interface ChapterDao {
    @Update
    suspend fun update(chapter: Chapter)

    @Insert
    suspend fun insert(chapter: Chapter)

    // 更新章节标题
    @Query("UPDATE chapter SET title = :title WHERE url = :chapterUrl")
    suspend fun updateChapterTitle(title: String?, chapterUrl: String)

    // 将章节标记为未读
    @Query("UPDATE chapter SET read = 0 WHERE url = :chapterUrl")
    suspend fun markChapterAsUnread(chapterUrl: String)

    // 将章节标记为已读
    @Query("UPDATE chapter SET read = 1 WHERE url = :chapterUrl")
    suspend fun markChapterAsRead(chapterUrl: String)
}
```

### 用户账号和配置

除了图书的数据库定义，APP还使用了sharePreferences保存用户账号和配置信息

- 定义一个Account类表示用户信息，并封装了sharePreferences获取和修改用户信息

```kotlin
data class Account(
    val userId: Int,
    val role: String,
    val username: String,
    val email: String,
    val phoneNumber: String,
    val introduction: String,
    val nickname: String,
    val level: Int,
    val exp: Int,
    val avatar: String,
    val gender: String
) {
    companion object {
        private const val PREFS_NAME = "userInfo"
        private const val KEY_USER_ID = "user_id"
        private const val KEY_ROLE = "role"
        private const val KEY_USERNAME = "username"
        private const val KEY_EMAIL = "email"
        private const val KEY_PHONE_NUMBER = "phone_number"
        private const val KEY_INTRODUCTION = "introduction"
        private const val KEY_NICKNAME = "nickname"
        private const val KEY_LEVEL = "level"
        private const val KEY_EXP = "exp"
        private const val KEY_AVATAR = "avatar"
        private const val KEY_GENDER = "gender"

        private lateinit var sharedPreferences: SharedPreferences

        fun init(context: Context):SharedPreferences {
            sharedPreferences = context.getSharedPreferences(PREFS_NAME, Context.MODE_PRIVATE)
            return sharedPreferences
        }

        fun getRef(): SharedPreferences {
            return sharedPreferences
        }

        fun save(account: Account) {
            val editor = sharedPreferences.edit()
            editor.putInt(KEY_USER_ID, account.userId)
            editor.putString(KEY_ROLE, account.role)
            editor.putString(KEY_USERNAME, account.username)
            editor.putString(KEY_EMAIL, account.email)
            editor.putString(KEY_PHONE_NUMBER, account.phoneNumber)
            editor.putString(KEY_INTRODUCTION, account.introduction)
            editor.putString(KEY_NICKNAME, account.nickname)
            editor.putInt(KEY_LEVEL, account.level)
            editor.putInt(KEY_EXP, account.exp)
            editor.putString(KEY_AVATAR, account.avatar)
            editor.putString(KEY_GENDER, account.gender)
            editor.apply()
        }

        fun get(): Account {
            val userId = sharedPreferences.getInt(KEY_USER_ID, -1)
            val role = sharedPreferences.getString(KEY_ROLE, "") ?: ""
            val username = sharedPreferences.getString(KEY_USERNAME, "") ?: ""
            val email = sharedPreferences.getString(KEY_EMAIL, "") ?: ""
            val phoneNumber = sharedPreferences.getString(KEY_PHONE_NUMBER, "") ?: ""
            val introduction = sharedPreferences.getString(KEY_INTRODUCTION, "") ?: ""
            val nickname = sharedPreferences.getString(KEY_NICKNAME, "") ?: ""
            val level = sharedPreferences.getInt(KEY_LEVEL, 0)
            val exp = sharedPreferences.getInt(KEY_EXP, 0)
            val avatar = sharedPreferences.getString(KEY_AVATAR, "") ?: ""
            val gender = sharedPreferences.getString(KEY_GENDER, "") ?: ""
            return Account(
                userId,
                role,
                username,
                email,
                phoneNumber,
                introduction,
                nickname,
                level,
                exp,
                avatar,
                gender
            )
        }
    }
}
```

- 登录成功后保存用户信息

```kotlin
binding.login.setOnClickListener {
	val username = binding.username.editText?.text.toString()
	val password = binding.password.editText?.text.toString()
	Valid.isValidUsername(username)?.let {
		SnackbarUtil.showWarningMessage(binding.root, "请正确填写用户名")
		return@setOnClickListener
	}
	Valid.isValidPassword(password)?.let {
		SnackbarUtil.showWarningMessage(binding.root, "请正确填写密码")
		return@setOnClickListener
	}
	val remember = binding.rememberMe.isChecked

	val call = apiService.login(username, password, remember)
	Requests.enqueue(call, binding.root, success = { message, account ->
		SnackbarUtil.showSuccessMessage(binding.root, message)
		// 登录成功，保存用户信息跳转到 MainActivity
		Account.init(this.requireContext())
		if (account != null) {
			Account.save(account)
		}
		interactionListener?.toMain()
	})
}
```

- 使用adb shell 连接到数据库

```sql
CREATE TABLE `Book` (
	`isbn` TEXT, `bookId` INTEGER NOT NULL, 
	`title` TEXT NOT NULL, `author` TEXT, 
	`publisher` TEXT, `publishDate` TEXT, 
	`language` TEXT, `collectCount` INTEGER NOT NULL, 
	`description` TEXT, 
	`price` TEXT, 
	`coverImage` TEXT, 
	`ratingNUm` TEXT, 
	`completed` INTEGER NOT NULL, 
	`inLibrary` INTEGER NOT NULL, 
	`lastReadEpochTimeMilli` INTEGER NOT NULL, 
	PRIMARY KEY(`bookId`)
);
CREATE TABLE `Chapter` (
	`title` TEXT NOT NULL, 
	`url` TEXT NOT NULL, 
	`bookId` INTEGER NOT NULL, 
	`position` INTEGER NOT NULL, 
	`read` INTEGER NOT NULL, 
	`lastReadPosition` INTEGER NOT NULL, 
	`lastReadOffset` INTEGER NOT NULL, 
	`body` TEXT NOT NULL, PRIMARY KEY(`url`)
);
```

![](https://pan.lmio.xyz/pic/d0ba87ffa658984af4fb2975c8c1c0f9.png)

通过android可以看到数据库运行正常

![image.png](https://pan.lmio.xyz/pic/b2a5a2d407e5dfd2e6a127f4e4ff5074.png)


### 数据库操作

数据库操作不可以在ui线程进行，要使用异步任务或者协程

```kotlin
val db = AppDatabase.createRoom(applicationContext)  
  
// 在kotlin协程中执行数据库操作  
GlobalScope.launch(Dispatchers.IO) {  
	db.insert(book)
	...  
}
```

通过appDatabase类可以很简单地操作数据库

## 实验总结

本次实验主要是围绕 Android 应用中的数据库操作展开的。通过实验，我深入了解了 SQLite 数据库的基本原理和使用方法，掌握了使用 adb shell 命令创建数据库的方法，同时也学会了使用 Room 操作 SQLite 数据库的方法。


## 实验感想
在这次关于 Android 开发的实验中，我学到了很多关于 Android 应用开发的知识和技巧。通过实现一个简单的图书管理应用。

我发现了在 Android 应用中使用 SQLite 数据库需要注意的一些问题，例如在主线程上执行数据库操作可能会导致应用卡顿或崩溃，因此需要使用异步任务或 Kotlin 协程来避免这个问题。

在进行数据库操作时，为了保证数据的一致性和完整性，我们需要使用事务处理机制。为了加快数据库查询速度，我使用了索引。

总的来说，这次实验让我深入了解了 Android 应用开发的一些关键技术和实践，也让我更加熟悉了 Android Studio 和 Kotlin 编程语言。我相信这些知识和技能将对我今后的学习和工作都有很大的帮助。


