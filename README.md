## 技术

1. Wepy （开发框架）
2. iview weapp (UI 库)
3. zanui weapp (UI 库)

## 开发准备工作
1. 前往 https://mp.weixin.qq.com ，注册小程序账号，拿到 AppId。

2. 登录 https://mp.weixin.qq.com ，就可以在网站的“设置”-“开发者设置”中，查看到微信小程序的 AppID 了，注意不可直接使用服务号或订阅号的 AppID 。 

3. [下载开发工具](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html?t=1476197489869)，并安装。

4. 建立项目
开发者工具安装完成后，打开并使用微信扫码登录。选择创建“项目”，填入上面步骤获取到的 AppID ，设置一个本地项目的名称（非小程序名称）。

### 开发
1. 安装[开发工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html?t=2018125)
2. 扫码登入
3. 创建项目
4. 可在模拟器中运行小程序

### 手机调试
1. 注册小程序微信工作平台
2. 设置 appid
3. 将自己的微信行添加远程调试权限
4. 微信小程序需要在后台添加开发者和体验者，如此可多人协助检视。
    * 开发者：增加开发人员的，开发人员添加后，可上传代码，最多10个人，可以删除
    * 体验者：添加为体验者，管理员发布体验版本后，通过扫码二维码可以下载体验版小程序，最多20个人，添加人后是可以删除的


### 关于小程序

1. 小程序重新定义了DOM结构，没有 window、document、div、span等，小程序只有view、text、image等 封装好的组件
2. 小程序没有cookie，只能通过storage来模拟各项cookie操作（包括http中的setCookie也需要自行处理）

#### 小程序渲染对应环境

* ISO -> JavascriptCore
* android -> X5 内核
* IED -> nwjs

所以三个环境里的表现会不一样，勿依赖开发环境的正确结果。


[scrollview](https://www.jianshu.com/p/f6d771421eb9)




