# fragment

### 循环渲染组件
```
# wepy 提供的repeat组件
<view class="movie" wx:if="{{movies}}">
  <repeat for="{{movies}}" key="index" index="index" item="item">
    <movie :movie.sync="item"></movie>
  </repeat>
</view>
```

```
# 微信提供的block组件
<block wx:for="{{imgArr}}" wx:key="index">
  <swiper-item class="item" data-movieId="{{item.id}}" @tap="showMovieDetail">
    <image class="img" src="{{item.img || item.image}}"></image>
  </swiper-item>
</block>
```