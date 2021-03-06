# 声明

『知乎』是 知乎. Inc 的注册商标。本软件与其代码非由知乎创作或维护。软件中所包含的信息与内容皆违反版权与知乎用户协议。本项目所有文字图片等稿件内容均由知乎提供，获取与共享之行为或有侵犯知乎权益的嫌疑。若被告知需停止共享与使用，本人会及时删除整个项目。请您了解相关情况，并遵守知乎协议。

# 前言

出于对知乎日报的喜爱，做了一个vue版本的**高仿**知乎日报。

## 技术栈

vue2.x + vuex + vue-router + axios + ES6 + sass + localStorage

## 知乎日报API 数据接口

参考: [http://blog.csdn.net/fanpeihua123/article/details/51210499](http://blog.csdn.net/fanpeihua123/article/details/51210499)

## 项目运行

```
git clone https://github.com/zhijiang3/vue-zhihu-daily.git

cd vue2-zhihu-daily

# 安装依赖文件
npm install

# 启动项目
npm run dev
```

# 遇到的问题汇总

1. 代理服务器后，请求到的图片不显示的问题。解决办法：在 **&lt;head&gt;** 中添加 **&lt;meta name="referrer" content="never"&gt;** 就ok了。  
meta标签大全参考：[http://blog.csdn.net/kongjiea/article/details/17092413](http://blog.csdn.net/kongjiea/article/details/17092413)

2. 动画效果很卡。解决办法：利用 **will-change** 或 **transform** 属性的一些3d方法，调起硬件加速，如：**transform: translate3d(0, 0, 0);**、**will-change: transform;**

3. 因为针对轮播和刷新添加 **touch** 事件，轮播和下拉刷新冲突了，在下拉刷新时，轮播会暂停。这里没解决，建议 **touch** 事件加在 **document** 上，利用 **e.target** 判断是否是需要的节点

4. 偶然发现手机浏览某些网址，如：[百度](https://www.baidu.com)，在下滑时，地址栏会隐藏起来。搜了一下可以通过 **window.scrollTo(0, 1)** 
实现这个效果。此项目未能实现这个效果，因为高度是自适应的没找到解决办法。  
参考地址: [https://github.com/scottjehl/Hide-Address-Bar](https://github.com/scottjehl/Hide-Address-Bar)

# 目标功能
- [x] 日间/夜间模式 —— √
- [x] 无图模式(内容不加载图片) —— √
- [x] 滚动到底部自动加载数据 —— √
- [x] 首页顶部的标题跟随栏目标题 —— √
- [x] 离线下载 —— √，图片部分能加载，一部分需要联网（不消耗流量）才能查看
- [x] 双击主页标题可回到顶部 —— √
- [x] 轮播图效果 —— √ 和下拉刷新有冲突，在下拉刷新时，轮播会暂停
- [x] 下拉刷新 —— √ 和banner有冲突，在下拉刷新时，轮播会暂停
- [x] 点击评论里省略的回复可以展开或收回 —— √
- [x] 收藏文章功能 —— √ 不用登陆，存储在localStorage
- [ ] 分享
- [ ] 内容点击图片放大
- [ ] 子栏目过渡动画
- [ ] 内容左右滑动切换

# 未能实现功能

### 由于以下功能没有提供 API 所以没法做的

- [ ] 登陆
- [ ] 消息功能
- [ ] 点赞/评论点赞
- [ ] 回复和评论功能

# 部分截图

### 切换皮肤

![切换皮肤](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/1.gif)

### 收藏

![收藏](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/2.gif)

### 查看评论

![查看评论](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/3.gif)

### 双击标题回到顶部

![双击标题回到顶部](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/4.gif)

### 主题日报和主题编辑

![主题日报和主题编辑](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/5.gif)

### 刷新

![刷新](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/6.gif)

### 离线下载

![离线下载](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/7.gif)

### 不加载图片内容

![不加载图片内容](https://github.com/zhijiang3/vue-zhihu-daily/blob/master/static/demo/8.gif)

# 项目布局

```
├─build                 webpack配置文件
├─config                项目配置
├─src                   源码目录
│  ├─api                api接口
│  │  └─news.js         新闻的api接口
│  ├─common             公共组件
│  │  ├─fonts           字体
│  │  ├─js              脚本
│  │  └─scss            样式
│  ├─components         组件文件夹
│  │  ├─banner          轮播图组件
│  │  ├─column          栏目组件
│  │  ├─commentitem     单个评论组件
│  │  ├─item            单个列表组件
│  │  ├─menulist        菜单列表组件
│  │  ├─navigation      导航组件
│  │  ├─news            新闻组件
│  │  ├─refresh         刷新组件
│  │  └─sidebar         侧边栏组件
│  ├─router             路由文件夹
│  │  └─index.js        配置路由
│  ├─store              vuex状态管理
│  │  └─index.js        创建store
│  ├─views              视图文件夹
│  │  ├─collection      查看收藏的内容视图
│  │  ├─comment         评论视图
│  │  ├─detail          详情页视图
│  │  ├─editor          主编详情视图
│  │  ├─editors         主编视图
│  │  ├─index           主页视图
│  │  ├─option          设置选项视图
│  │  ├─section         栏目(合集)视图
│  │  └─theme           主题日报视图
│  ├─App.vue            挂载入口
│  └─main.js            vue实例生成与挂载
├─static                静态资源
├─index.html            网页入口
```
