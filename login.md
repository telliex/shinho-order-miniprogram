# 小程序登入流程

![微信](https://files.jb51.net/file_images/article/201804/20184984148499.jpg?20183984355)

1. wx.login() 为当前用户生成一个临时的登录凭证，临时登录凭证的有效期只有五分钟。每次调用 wx.login() ，都会下发一个新的 code 和再透过服务器去取回去对应的session_key （下方步骤）

```
wx.login({
  success: function(loginRes) {
   if (loginRes.code) {
    // example: 081LXytJ1Xq1Y40sg3uJ1FWntJ1LXyth
   }
  }
});

// 回传
{errMsg: "login:ok", code: "002osFfj0FOKJn1PFDij0JoDfj0osFfB"}

```

2. 获取 openid 和 session_key
 - openid - 标识每个用户在订阅号、服务号、小程序这三种不同应用的唯一标识
 - session_key - 让该用户进行登录，那么 session_key 就保证了当前用户进行会话操作的有效性，
 这个session_key是微信服务端给我们派发的。在自己的服务端请求微信提供的第三方接口 https://api.weixin.qq.com/sns/jscode2session 。避免将我们小程序的  appid 和小程序的 secret 暴露在外部，同时也将微信服务端下发的 session_key 暴露
 
| 参数 | 值 |
| - | - |
| appid	| 小程序的appid |
| secret |小程序的secret |
| js_code | 前面调用wx.login派发的code |
| grant_type |'authorization_code' |

3. 服务器使用不可逆的哈希算法，比如md5、sha1等生成 skey 给前端，并在前端维护这份登录态标识 (一般是存入 storage )

session_key获取的流程

（1）注册微信小程序、登录后台在设置中获得 appId 和 secret (密钥)
（2）调用 wx.login() 接口获取登录凭证 js_code
（3）调用 wx.request() 接口把js_code发送到服务器后台
（4）在服务器后台，已知 appId、secret、js_code
然后调用如下官方提供的http接口，即可返回获取openId、session_key

官方提供了http接口地址为：
https://api.weixin.qq.com/sns/jscode2session?appid=APPID&secret=SECRET&js_code=JSCODE&grant_type=authorization_code


4. 如果当前 session_key 过期，就让用户来重新登录，更新 session_key，并将最新的 skey 存入用户数据表中。

![](https://files.jb51.net/file_images/article/201804/20184984837214.png?20183984849)

```
let loginFlag = wx.getStorageSync('skey');
if (loginFlag) {
 // 检查 session_key 是否过期
 wx.checkSession({
 // session_key 有效(未过期)
 success: function() {
  // 业务逻辑处理
 },
  
 // session_key 过期
 fail: function() {
  // session_key过期，重新登录
  doLogin();
 }
 });
) else {
 // 无skey，作为首次登录
 doLogin();
}
```