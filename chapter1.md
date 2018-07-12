# WePY


WePY的安装或更新都通过npm进行。

全局安装或更新WePY命令行工具
```
npm install wepy-cli -g
```

在开发目录中生成Demo开发项目
```
wepy init standard my-project
```

进入项目目录
```
cd myproject
```

安装依赖
```
npm install
```

开启实时编译
```
wepy build --watch
```




1. 小程序重新定义了DOM结构，没有window、document、div、span等，小程序只有view、text、image等 封装好的组件
2. 小程序没有cookie，只能通过storage来模拟各项cookie操作（包括http中的setCookie也需要自行处理）

wepy框架

## IDE 编辑器下，wepy 代码的高亮 

在插件目录搜索安装 vetur，或者 vue，点击 VS Code 右下角的语言，选择 “.wpy” 的配置文件关联，然后选择 Vue，即可启动代码高亮。



坑
1. WePY中的methods属性只能声明页面wxml标签的bind、catch事件，不能声明自定义方法，这与Vue中的用法是不一致的。普通自定义方法在methods对象外声明，与methods平级。
2. 变量与方法尽量使用驼峰式命名，并且注意避免使用$开头。 以$开头的标识符为WePY框架的内建属性和方法，
3. 原 bindtap="click" 替换为 @tap="click"，原catchtap="click"替换为@tap.stop="click"。原 capture-bind:tap="click" 替换为 @tap.capture="click"，原capture-catch:tap="click"替换为@tap.capture.stop="click"。
4. 事件传参使用优化后语法代替。 原bindtap="click" data-index={{index}}替换为@tap="click({{index}})"。
5. WePY中，在父组件template模板部分插入驼峰式命名的子组件标签时，不能将驼峰式命名转换成短横杆式命名(比如将childCom转换成child-com)，这与Vue中的习惯是不一致。
6. 
```
<repeat for="{{list}}" key="index" index="index" item="item">
        <!-- 插入<script>脚本部分所声明的child组件，同时传入item -->
        <child :item="item"></child>
    </repeat>
```


https://hacpai.com/article/1523346638650



[微信小程序优秀开发资源汇总](https://juejin.im/entry/5a9dfb9b5188255568683d3c)
[微信小程序常见的UI框架/组件库总结](https://www.jianshu.com/p/429529867818)
[全网最全的小程序学习资料和文章，看这篇就够了](https://www.jianshu.com/p/965aa85debd1)




* 当值默认为auto时，以此元素设置的尺寸为准，若也是auto，则以内容content尺寸为准
* 当flex-basis设置了值时，以此设置尺寸的为准
* 若为百分比，则根据父容器进行计算。若为0%，则其设置的width将无效。
* 建议在子项中通过设置flex-basis的方式去设置想要的尺寸，而不是设置width
* 缩写flex:auto(flex: 1 1 auto)，flex:none(0 0 auto)，flex:1(1 1 0%)
* 若想某项不参与弹性布局的计算，应将其设置成flex:none