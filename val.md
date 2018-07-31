### 父子组件传值通信

```
props: {
    phone: {            // 属性名
      type: Number,     // 类型（必填），目前接受的类型包括：String, Number, Boolean, Object, Array, null（表示任意类型）
      value: ''     // 属性初始值（可选），如果未指定则会根据类型选择一个
    }
  }
```

一个页面转到另一个页面，一般情况下可以通过navigate或redirect时候的url来携带参数，方式只有在目标页面还没有创建的时候，才有效。因为一个页面的onLoad方法在页面的生命周期中，只执行一次。
```

// 源页面A相关代码
wx.navigateTo({
  url: "/pages/mypage/mypage?a=1&b=2"
})
 
// 目标页面B相关代码
Page({
  onLoad: function (options) {
    var a = options.a; // 值：1
    var b = options.b; // 值：2
  }

```

### 方法1：使用全局数据存储
```
//=== 1. 存储到app对象上的方式 ========
var app = getApp()
app.globalData.mydata = {a:1, b:2};  //存储数据到app对象上
wx.navigateBack();  //返回上一个页面
 
//=== 2.存储到数据缓存的方式 =========
wx.setStorage({
  key: "mydata",
  data: {a:1, b:2},
  success: function () {
    wx.navigateBack();   //返回上一个页面
  }
```
### 从页面路由栈中直接获取和操作目标Page对象

```

var pages = getCurrentPages();
var currPage = pages[pages.length - 1];   //当前页面
var prevPage = pages[pages.length - 2];  //上一个页面
 
//直接调用上一个页面的setData()方法，把数据存到上一个页面中去
prevPage.setData({
  mydata: {a:1, b:2}

```

### 传值
```
<view data-index="{{index}}" bindtap="delete"><image src="../../../images/icon_delete.png" /><text>删除</text></view>

delete: function (e) {
  var index = parseInt(e.currentTarget.dataset.index);
  console.log("index" + index);
}
```