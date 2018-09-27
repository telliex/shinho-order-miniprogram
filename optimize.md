# 小程序优化

因小程序 2M 限制，上线前需要经过压缩。

## 资源压缩

大部分资源都可以进行适当压缩，常常可以在保证功能体验的同时，有效地减少空间占用。

参考工具：

* js压缩: 配置wepy-plugin-uglifyjs插件
* json、wxml压缩： 配置wepy-plugin-filemin插件
* less压缩： 配置wepy-compiler-less插件
* 图片压缩： 配置wepy-plugin-imagemin插件、TinyPNG