## 开发准备工作
1. 登录 https://mp.weixin.qq.com ，就可以在网站的“设置”-“开发者设置”中，查看到微信小程序的 AppID 了，注意不可直接使用服务号或订阅号的 AppID 。 

2. 下载开发工具
[下载地址](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html?t=1476197489869)

3. 建立项目
开发者工具安装完成后，打开并使用微信扫码登录。选择创建“项目”，填入上面步骤获取到的 AppID ，设置一个本地项目的名称（非小程序名称）

# My Awesome Book

小程序后台登录网址：https://mp.weixin.qq.com/


[微信小程序基础：天气应用?](https://classroom.udacity.com/courses/ud666-cn-1)

### 注册账号
注册小程序账号，拿到 AppId。

### 开发
1. 安装[开发工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html?t=2018125)
2. 扫码登入
3. 创建项目
4. 可在模拟器中运行小程序

### 手机调试
1. 注册小程序微信工作平台
2. 设置 appid
3. 将自己的微信行添加远程调试权限

微信小程序需要在后台添加开发者和体验者

开发者：增加开发人员的，开发人员添加后，可上传代码，最多10个人，可以删除

体验者：添加为体验者，管理员发布体验版本后，通过扫码二维码可以下载体验版小程序，最多20个人，添加人后是可以删除的

[API请求](https://developers.weixin.qq.com/miniprogram/dev/api/network-request.html)
[生命周期](https://blog.csdn.net/qq_26585943/article/details/54407202)

[scrollview](https://www.jianshu.com/p/f6d771421eb9)

[深入 wepy 小程序组件化框架](https://toutiao.io/posts/zvnb1h/preview)
[深入 wepy 小程序组件化框架](https://imhjm.com/article/5977ebab7dd03248a2e8d57f)
[Icon-font图标字体的四类制作方法](https://www.jianshu.com/p/095eb298ed18)

icon lib
[icomoon](https://icomoon.io/)
[fontawesome](http://fontawesome.dashgame.com/)
[ionicons](https://ionicons.com/)
[fontello](http://fontello.com/)


资源压缩

大部分资源都可以进行适当压缩，常常可以在保证功能体验的同时，有效地减少空间占用。参考工具：

js压缩: 配置wepy-plugin-uglifyjs插件
json、wxml压缩： 配置wepy-plugin-filemin插件
less压缩： 配置wepy-compiler-less插件
图片压缩： 配置wepy-plugin-imagemin插件、TinyPNG