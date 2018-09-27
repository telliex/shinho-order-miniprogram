# 开发中采过的坑

## 几点须知
#### 1. wepy 中使用 wx:if，只阻止视图渲染，不会阻止组件初始化。

#### 2. 图片引入正常,但是无缘无故报错问题

原因:在于初始化的时候,变量还没渲染进去,导致src为错误的值,
解法:

```
<image wx:if="{{postData.avatar}}" class="avatar" src="{{postData.avatar}}"></image> 
```

#### 3. 微信小程序界面跳转传 json 对象,出现 object 对象变字串

解法:
将 JSON 转成字符串传值 `JSON.stringify(user)`;
将字符串转成对象接收 `JSON.parse(options.userStr)`;

```
# 传值 js (母页面)
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

# 接收 js (目标页面)
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

#### 4. this.$parent 更改没反应

需要多加
```
this.$parent.$apply();
```

#### 5. component 可以使用 parent 的 usingComponents ，若是跳转的页面及无法。

#### 6. 若 onLoad() 因为是组件在进画面时已被加载，可加入 `this.$apply()` 帮助进画面时重新渲染

#### 7. 微信小程序的网络请求必须走Https协议，就是说微信小程序一定要通过HTTPS加密。 

#### 8. page 呼叫 global => this.$parent;

#### 9. page里的子组件呼叫 global => this.$root.$parent;

#### 10. 价钱的加减乘除会有出现浮点数，如 12.0000000000001
解法:
[浮点数计算 bug](https://blog.csdn.net/helloxiaoliang/article/details/72723387)

#### 11. 如何让小程序有类似 cookie 功能
解法:
[仿 cookie](https://www.csweigou.com/article/2143.html)

#### 12. 抓取 目标 DOM 

```
  that.$apply();
  var query = wx.createSelectorQuery();
  query.select('.aslide-item-info').boundingClientRect();
  query.exec(function(res) {
    console.log(res);
  that.boxHeight = res[0].height;
  });
```

#### 13. textarea 高度永远最高，且卷动时会出现异常，此部份尚无解，仅能用条件判断避开
解法:
[textarea 坑](http://www.wxapp-union.com/forum.php?mod=viewthread&tid=3270)

当前小程序作法：
1. 上方有物件时,让文字区块隐藏，如优惠券浮窗
2. 卷动时文字停留 bug ，做一个伪文字区块(以 view 模拟)，编辑时点击伪文字区块，换成 该 textarea，unfocus 或卷动视窗时，又切回伪文字区块，并将编辑内容放入。

