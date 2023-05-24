## 一、实验目的
	应用 Web 测试工具对 Web 系统进行功能和性能测试

## 二、实验原理

	Web测试是对Web系统进行多方面测试，包括功能、性能、可用性、安全性等方面。具体来说，可以分为以下几个方面：

### 一、功能测试

对Web系统进行功能测试包括以下几个方面：

1.链接测试

链接是Web应用系统的一个主要特征，它是在页面之间切换和指导用户去一些不知道地址的页面的主要手段。链接测试可分为三个方面。首先，测试所有链接是否按指示的那样确实链接到了该链接的页面；其次，测试所链接的页面是否存在；最后，保证Web应用系统上没有孤立的页面，所谓孤立页面是指没有链接指向该页面。

2.表单测试

当用户给Web应用系统管理员提交信息时，就需要使用表单操作，例如用户注册、登陆、信息提交等。在这种情况下，我们必须测试提交操作的完整性，以校验提交给服务器的信息的正确性。例如：用户填写的出生日期与职业是否恰当，填写的所属省份与所在城市是否匹配等。如果使用了默认值，还要检验默认值的正确性。如果表单只能接受指定的某些值，则也要进行测试。例如：只能接受某些字符，测试时可以跳过这些字符，看系统是否会报错。

3.Cookies测试

Cookies通常用来存储用户信息和用户在应用系统的操作，当一个用户使用Cookies访问了某一个应用系统时，Web服务器将发送关于用户的信息，把该信息以Cookies的形式存储在客户端计算机上，这可用来创建动态和自定义页面或者存储登陆等信息。如果Web应用系统使用了Cookies，就必须检查Cookies是否能正常工作。测试的内容可包括Cookies是否起作用，是否按预定的时间进行保存，刷新对Cookies有什么影响等。

4.数据库测试

在Web应用技术中，数据库起着重要的作用，数据库为Web应用系统的管理、运行、查询和实现用户对数据存储的请求等提供空间。在使用了数据库的Web应用系统中，一般情况下，可能发生两种错误，分别是数据一致性错误和输出错误。数据一致性错误主要是由于用户提交的表单信息不正确而造成的，而输出错误主要是由于网络速度或程序设计问题等引起的，针对这两种情况，可分别进行测试。

### 二、性能测试

对Web系统进行性能测试主要包括以下几个方面：

1.连接速度测试

用户连接到Web应用系统的速度根据上网方式的变化而变化，他们或许是电话拨号，或是宽带上网。当下载一个程序时，用户可以等较长的时间，但如果仅仅访问一个页面就不会这样。如果Web系统响应时间太长（例如超过5秒钟），用户就会因没有耐心等待而离开。另外，有些页面有超时的限制，如果响应速度太慢，用户可能还没来得及浏览内容，就需要重新登陆了。而且，连接速度太慢，还可能引起数据丢失，使用户得不到真实的页面。

2.负载测试

负载测试是为了测量Web系统在某一负载级别上的性能，以保证Web系统在需求范围内能正常工作。负载级别可以是某个时刻同时访问Web系统的用户数量，也可以是在线数据处理的数量。例如：Web应用系统能允许多少个用户同时在线？如果超过了这个数量，会出现什么现象？Web应用系统能否处理大量用户对同一个页面的请求？

3.压力测试

进行压力测试是指实际破坏一个Web应用系统，测试系统的反映。压力测试是测试系统的限制和故障恢复能力，也就是测试Web应用系统会不会崩溃，在什么情况下会崩溃。黑客常常提供错误的数据负载，直到Web应用系统崩溃，接着当系统重新启动时获得存取权。压力测试的区域包括表单、登陆和其他信息传输页面等。

### 三、可用性测试

1.导航测试

导航描述了用户在一个页面内操作的方式。通过考虑下列问题，可以决定一个Web应用系统是否易于导航：导航是否直观？Web系统的主要部分是否可通过主页存取？Web系统是否需要站点地图、搜索引擎或其他的导航帮助？

2.图形测试

一个Web应用系统的图形可以包括图片、动画、边框、颜色、字体、背景、按钮等。图形测试的内容有：（1）确保图形有明确的用途，图片或动画不要胡乱地堆在一起，以免浪费传输时间。（2）验证所有页面字体的风格是否一致。（3）背景颜色应该与字体颜色和前景颜色相搭配。（4）图片的大小和质量也是一个很重要的因素，一般采用JPG或GIF压缩。

3.内容测试

内容测试用来检验Web应用系统提供信息的正确性、准确性和相关性。

4.整体界面测试

整体界面是指整个Web应用系统的页面结构设计，是给用户的一个整体感。对整体界面的测试过程，其实是一个对最终用户进行调查的过程。一般Web应用系统采取在主页上做一个调查问卷的形式，来得到最终用户的反馈信息。

## 三、实验步骤

### 题目一：测试网站功能选择一个网站，对其进行功能测试。要求首先编写测试用例，然后用QuickTestProfessional自动化测试工具对该网站进行测试。
	选择本地搭建的网站，只有简单的登陆注册和忘记密码后端使用springboot（http://localhost:4173），进行测试

#### 网站页面
- 登陆页面
![](https://pan.lmio.xyz/pic/8b386f2c85ca8a41b44fdc09ad5228fc.png)

- 忘记密码
![image.png](https://pan.lmio.xyz/pic/bab458cc3a9991c740cdb7bf40e50360.png)
- 用户注册页面
![image.png](https://pan.lmio.xyz/pic/ca9ea4be88298cf49a91ac902a08cc59.png)

- 404
![image.png](https://pan.lmio.xyz/pic/d4dfe5180dda018a4e93f5b2948d8fab.png)


#### 链接测试
- 设计测试用例

| 编号 | url                                 |
|:---|:------------------------------------|
|  1 | http://localhost:4173/auth/register |
|  2 | http://localhost:4173/auth/login    |
|  3 | http://localhost:4173/auth/forget   |  

- 测试程序

```go
package webtest

import (
	"net/http"
	"testing"
)

func TestLinkTest(t *testing.T) {
	urls := []string{
		"http://localhost:4173",
		"http://localhost:4173/auth/login",
		"http://localhost:4173/auth/login",
		"http://localhost:4173/index",
	}

	for _, url := range urls {
		response, err := http.Get(url)
		if err != nil {
			t.Errorf("%s 请求错误: %s", url, err)
			continue
		}
		defer response.Body.Close()

		if response.StatusCode != http.StatusOK {
			t.Errorf("获取 %s 失败. 状态码: %d", url, response.StatusCode)
		}
	}
}
```


#### 表单测试

- 设计测试用例（使用边界测试）

```java
    @PostMapping("/register")
    public RestBean<String> registerUser(@Pattern(regexp = USERNAME_REGEX) @Length(min = 3, max = 10) @RequestParam("username") String username,
                                         @Length(min = 6, max = 16) @RequestParam("password") String password,
                                         @Pattern(regexp = EMAIL_REGEX) @RequestParam("email") String email,
                                         @Length(min = 6, max = 6) @RequestParam("code") String code) {
        String message = service.validateAndRegister(username, password, email, code);
        if(message == null) {
            return RestBean.success("注册成功");
        }else {
            return RestBean.failure(400, message);
        }
    }
```

根据后端api的限制

|        输入条件            |  有效等价类               |  编号    |  无效等价类                 |  编号  |
|:-----------------------|:---------------------|:-------|:-----------------------|:-----|
| 用户名长度                  |                 3-10 |  1     | &lt;3                  |    6 |
|                        |                      |        | &gt;10                 |    7 |
| 密码长度                   |                 6-16 |      2 | &lt;6                  |    8 |
|                        |                      |        | &gt;16                 |    9 |
| 邮箱格式                   | 有效邮箱                 |      3 | 不包含@                   |   10 |
|                        |                      |        | 没有.                    |   11 |
|                        |                      |        | 其他                     |   12 |
| 验证码长度                  |                    6 |      4 | &gt;6                  |   13 |
|                        |                      |        | &lt;6                  |   14 |
| 验证码是否有效                | 是                    |      5 | 否                      |   15 |  

- 测试用例

|  Username   |  Password            |  Email          |  Verification Code  |  Expected Error Message     | 覆盖等价类 |  覆盖等价类  |
|:------------|:---------------------|:----------------|:--------------------|:----------------------------|:------|:--------|
|   12        |   123456             |  123@jl.com     |  123456             |  无效请求                       |     6 |       6 |
| 12345678901 |               123456 |      123@jl.com |              123456 | 无效请求                        |     7 |       7 |
|   1234      |  123                 |  123@jl.com     |              123456 |  无效请求                       |     8 |       8 |
|   1234      |   123456             |  123@jl.com     |  123456             |  请获取验证码后再试                  |    15 |      15 |
|   1234      |   12345670000000000  |  123@jl.com     |              123456 |  无效请求                       |     9 |       9 |
|   1234      |   123456             |  123j.com       |  123456             |  无效请求                       |    10 |      10 |
|        1234 |               123456 |       123@fdcom |              123456 | 无效请求                        |    11 |      11 |
|        1234 |               123456 | &amp;132@qq.com |              123456 | 无效请求                        |    12 |      12 |
|   1234      |               123456 |  123@jl.com     |             1234567 |  无效请求                       | 13,15 |  13, 15 |
|   1234      |               123456 |  123@jl.com     |  123                |  无效请求                       | 14,15 |  14, 15 |  


```go
import (
	"encoding/json"
	"io"
	"net/http"
	Url "net/url"
	"strings"
	"testing"
)

type RegistrationForm struct {
	Username   string
	Password   string
	Email      string
	VerifyCode string
}

const url = "http://localhost:8080/api/auth/register"

func TestRegistrationForm(t *testing.T) {
	testCases := []struct {
		form RegistrationForm
		expectedResult string
	}{
		{RegistrationForm{"12", "123456", "123@jl.com", "123456"}, "无效请求"},
		{RegistrationForm{"12345678901", "123456", "123@jl.com", "123456"}, "无效请求"},
		{RegistrationForm{"123", "123456", "123j.com", "123456"}, "无效请求"},
		{RegistrationForm{"1234", "123456", "123@jl.com", "123456"}, "请获取验证码后再试"},
		{RegistrationForm{"1234", "123456", "123j.com", "123456"}, "无效请求"},
		{RegistrationForm{"1234", "123456", "123@jl.com", "123"}, "无效请求"},
		{RegistrationForm{"1234", "1234", "123@jl.com", "1234567"}, "无效请求"},
		{RegistrationForm{"1234", "1234", "123@jl.com", "123456"}, "无效请求"},
		{RegistrationForm{"1234", "1234", "&132@qq.com", "123456"}, "无效请求"},
		{RegistrationForm{"1234", "12345670000000000", "123@jl.com", "123456"}, "无效请求"},
	}
	
	for _, tc := range testCases {
		res := submitRegistrationForm(tc.form)
		if res["message"] != tc.expectedResult {
			t.Errorf("表单%v, 返回值%v", tc.form, res["message"])
		}
	}
}

func submitRegistrationForm(form RegistrationForm) map[string]interface{} {
	// 构建 POST 请求的数据
	formData := Url.Values{
		"username": {form.Username},
		"password": {form.Password},
		"email":    {form.Email},
		"code":  {form.VerifyCode},
	}

	// 将表单数据编码为字符串
	formEncoded := formData.Encode()

	resp, err := http.Post(url,
        "application/x-www-form-urlencoded",
        strings.NewReader(formEncoded))
    if err != nil {
        return nil
    }
	defer resp.Body.Close()
	body, err := io.ReadAll(resp.Body)
	if err != nil {
        return nil
    }
	var responseData map[string]interface{}
	err = json.Unmarshal(body, &responseData)
	if err != nil {
		return nil
	}
	return responseData
}
```


### 数据库并发性能测试

- 测试程序

```go
package webtest
import (
	"fmt"
	"math/rand"
	"net/http"
	Url "net/url"
	"strings"
	"sync"
	"testing"
	"time"
)

var maxTime = 0.0

var minTime = 5.0

func TestLoginTimeoutRate(t *testing.T) {
	testCases := []struct {
		username string
		password string
	}{
		{"123", "123456"},
		{"admin", "123456"},
		{"1245", "1234567"},
		{"12344", "12341"},
	}

	// 100个并发进程
	concurrency := 100

	// 每个进程循环执行10次
	iterations := 10

	var wg sync.WaitGroup
	var mu sync.Mutex
	timeoutCount := 0

	for i := 0; i < concurrency; i++ {
		wg.Add(1)
		go func() {
			defer wg.Done()
			for j := 0; j < iterations; j+0.50秒+ {
				tc := testCases[rand.Intn(len(testCases))]
				if !Login(tc.username, tc.password) {
					mu.Lock()
					timeoutCount++
					t.Errorf("超时，超时次数%d", timeoutCount)
					mu.Unlock()
				}
				// 休眠随机时间，模拟请求间隔
				time.Sleep(time.Duration(rand.Intn(5)) * time.Second)
			}
		}()
	}

	wg.Wait()

	timeoutRate := float64(timeoutCount) / float64(concurrency*iterations) * 100

	fmt.Printf("超时次数: %d\n", timeoutCount)
	fmt.Printf("请求次数: %d\n", concurrency*iterations)
	fmt.Printf("超时概率: %.2f%%\n", timeoutRate)
	fmt.Printf("最低延迟：%.2f\n", minTime)
	fmt.Printf("最高延迟：%.2f\n", maxTime)
}

func Login(username string, password string) bool {
	// 构建 POST 请求的数据
	formData := Url.Values{
		"username": {username},
		"password": {password},
	}
	
	
	// 将表单数据编码为字符串
	formEncoded := formData.Encode()
	start := time.Now()
	_, err := http.Post("http://localhost:8080/api/auth/login", "application/x-www-form-urlencoded", strings.NewReader(formEncoded))
	if err != nil {
		return false
	}
	end := time.Now()
	duration := end.Sub(start)
	if duration > time.Duration(maxTime) * time.Second {
		maxTime = float64(duration.Seconds())
	}
	if duration < time.Duration(minTime) * time.Second {
		minTime = float64(duration.Seconds())
	}
	return duration < 5*time.Second
}
```



### 题目二：测试网站性能选择一个网站，对其进行性能测试。要求使用WebLoad进行压力测试。

	对baidu.com的主页进行性能测试

#### 网站加载数据的测试结果
![image.png](https://pan.lmio.xyz/pic/f6a9f17c143477869cdc60aca5f517ec.png)

#### 网站各项性能指标
![image.png](https://pan.lmio.xyz/pic/01c4278d84cd362b9f921dd7e12eb6ea.png)

#### 网页资源性能指标
![image.png](https://pan.lmio.xyz/pic/58ff4df45334121c793896e49b0b200d.png)

#### 根据分析报告，对网站性能改善的建议

  
1. 采用新一代格式提供图片               
	WebP 和 AVIF 等图片格式的压缩效果通常优于 PNG 或 JPEG，因而下载速度更快，消耗的数据流量更少
2. 推迟加载屏幕外图片
	所有关键资源加载完毕后再加载屏幕外图片和处于隐藏状态的图片，从而缩短可交互时间
3.  启用文本压缩
	对于文本资源，应先压缩（gzip、deflate 或 brotli），然后再提供，以最大限度地减少网络活动消耗的字节总数。

##  四、实验结果

- 链接测试

![image.png](https://pan.lmio.xyz/pic/b67abba4b4efe2b5690b67f121d4c006.png)

- 表单测试

![image.png](https://pan.lmio.xyz/pic/2e3ddb1cd1542ba246f93f48f1bc6878.png)

- 数据库并发性能测试

![image.png](https://pan.lmio.xyz/pic/a47f4db02035345c9b6d18d7a0a94771.png)



## 五、缺陷报告

1. 测试：功能测试 - 链接测试

- 缺陷1：网站中外部链接比较少，现存链接能够正常打开，当前还无法测试网站内容是否显示正常。
- 严重程度：低
- 备注：无

2.  测试：功能测试 - 注册表单验证

- 缺陷2：由于验证邮箱验证码不能编写程序测试的限制，无法对验证码进行测试。
- 预期结果：能够对所有字段进行测试。
- 实际结果：验证码字段只能人工测试。
- 严重程度：低

3. 测试：数据库并发性能测试 - 并发登陆请求
- 缺陷3：无法模拟较大并发量和数据吞吐量
- 预期测试：本来是想对数据库book表进行大规模并发测试，由于接口还没有完善，暂时搁浅
- 实际结果：使用golang进行小规模并发测试
- 严重程度：中等

6. 测试：性能测试 - Lighthouse 分析工具
- 缺陷4：性能指标不一致或错误的建议。
- 重现步骤：运行 Lighthouse 工具并检查报告中的性能指标和优化建议。
- 预期结果：报告中提供准确的性能指标和有效的优化建议。
- 实际结果：发现一些性能指标不一致或错误的优化建议。
- 严重程度：中等
- 备注：可能是工具版本、设置或测试环境等因素导致，需要进行更详细的调查和确认。