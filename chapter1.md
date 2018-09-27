# WePY


WePY 的安装或更新都通过 npm 进行。

全局安装或更新WePY命令行工具
```
npm install wepy-cli -g
```

在开发目录中生成 Demo 开发项目
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


## 使用 wepy 框架开发，注意事项
1. WePY 中的 methods 属性只能声明页面 wxml 标签的bind、catch事件，不能声明自定义方法，这与Vue中的用法是不一致的。普通自定义方法在 methods 对象外声明，与 methods 平级。
2. 变量与方法尽量使用驼峰式命名，并且注意避免使用 $ 开头。 以 $ 开头的标识符为WePY 框架的内建属性和方法，
3. 原 bindtap="click" 替换为 @tap="click"，原 catchtap="click"替换为@tap.stop="click"。原 capture-bind:tap="click" 替换为 @tap.capture="click"，原capture-catch:tap="click"替换为@tap.capture.stop="click"。
4. 事件传参使用优化后语法代替。 原bindtap="click" data-index={{index}}替换为@tap="click({{index}})"。
5. WePY 中，在父组件 template 模板部分插入驼峰式命名的子组件标签时，不能将驼峰式命名转换成短横杆式命名(比如将 childCom 转换成 child-com )，这与 Vue 中的习惯是不一致。
6. 使用方法 
```
<repeat for="{{list}}" key="index" index="index" item="item">
  <!-- 插入<script>脚本部分所声明的child组件，同时传入item -->
  <child :item="item"></child>
</repeat>
```

## 参考
* [Wepy](https://www.w3cschool.cn/qdwzc/qdwzc-t35y25tu.html)
* [深入 wepy 小程序组件化框架](https://toutiao.io/posts/zvnb1h/preview)
* [深入 wepy 小程序组件化框架](https://imhjm.com/article/5977ebab7dd03248a2e8d57f)
* [Wepy 坑](https://hacpai.com/article/1523346638650)



