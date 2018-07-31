
* wepy 中使用 wx:if，只阻止视图渲染，不会阻止组件初始化。

* 图片引入正常,但是无缘无故报错问题

原因:在于初始化的时候,变量还没渲染进去,导致src为错误的值,
解法:

```
<image wx:if="{{postData.avatar}}" class="avatar" src="{{postData.avatar}}"></image> 
```

* 微信小程序界面跳转传 json 对象,出现 object 对象变字串

解法:
将json转成字符串传值JSON.stringify(user);
将字符串转成对象接收 JSON.parse(options.userStr);

```
# 传值js
personInfoAction: function(event) {
     var user = this.data.user;
     //将json转成字符串
     let userStr=JSON.stringify(user);
     console.log(user);
    if(user) {
      wx.navigateTo({
        url: 'personInfo/index?userStr='+userStr,
        success: function(res){
          // success
        },
      })
    } else {
      wx.navigateTo({
        url: 'login/index',
        success: function(res){
          // success
        },
      })
    }
  }

# 接收js
onLoad: function(options) {
    console.log(options);
    //将字符串转成json
    let user = JSON.parse(options.userStr);
    console.log(user);
    this.setData({
      userListInfo: [ {
        title: '头像',
        subTitle: '',
        icon:'../../../images/icon_img_tx.png',//user.avatar,
        hasIcon:true
      },{
        title: '昵称',
        subTitle: user.nickname,
        icon:'',
        hasIcon:false
      }, {
        title: '手机号',
        subTitle: user.phone,
        icon:'',
        hasIcon:false
      }, {
        title: '实名认证',
        subTitle: user.truename,
        icon:'',
        hasIcon:false
      }]
    });
  }

```