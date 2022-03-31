# JLPT考试抢座脚本

这个脚本会调用网站原本的一些方法来是实现ajax请求，但去除了ui的各种操作，一遍更快的轮询和发起请求。


## 需要调整的参数
* 报考的等级
    
    `var examLevel = 2;`

* 目标考场

    `var targetAddr = ["1022101", "1022102"];`
    
    可通过 <https://jlpt.neea.cn/kdinfo.do?kdid=info> 查询
    

## 使用方法

- Chrome内核的浏览器打开 <https://jlpt.neea.cn/index.do>，登录帐号。
- F12打开控制台，会因为无限循环的debugger而进入断点调试。取消断点（Deactivate breakpoints），然后恢复运行（Resume script execution）。
- 来到Console界面，将所有代码粘贴进去，回车。
    - 刚运行或者验证码错误/过期之类的，会自动获取一个新的验证码，显示在控制台里。并弹出一个输入框，输入验证码答案后，程序继续运行。（不用区分大小写，会自动转大写）
    - 程序循环查询考场信息，找到符合目标条件的有座位考场，会立刻发起订座的请求。
- 一旦开启，在成功订座之前会不停循环。想要停止的话，有以下几种方法：
    - 在验证码输入框内填写exit。
    - 非验证码输入时，在控制台输入`stop()`并回车。
    - 直接关闭网页。