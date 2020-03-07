# vue-lyric

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run all tests
npm test
```

## 项目进化史

#### 1 搭建项目环境, 创建develop分支

```
vue init webpack vueShop

git checkout -b develop

autoOpenBrowser: true 			npm run dev 之后唤起浏览器
```

#### 2 项目的目录结构

```
api
common
components
fiters
mock
pages
router
store
App.vue
main.js
```

#### 3 安装stylus依赖包

``npm install stylus-loader --save-dev``

- 怎么理解stylus？

  ```
  使用stylus的时候自动整理代码的时候会出现大括号那些

  在setting.json中添加 就可以实现stylus的格式

  "stylusSupremacy.insertColons": false, // 是否插入冒号
  "stylusSupremacy.insertSemicolons": false, // 是否插入分好
  "stylusSupremacy.insertBraces": false, // 是否插入大括号
  "stylusSupremacy.insertNewLineAroundImports": false, // import之后是否换行
  "stylusSupremacy.insertNewLineAroundBlocks": false // 两个选择器中是否换行
  ```

  ​

#### 4 使用vscode配置vue常用的模板

- 安装VueHelper插件

- 寻找 `vue.json`

  按顺序点击vscode的：

  - 文件
  - 首选项
  - 用户代码片段
  - 接着搜索框中输入 `vue`， 回车

```
{
	"Print to console": {
        "prefix": "vue",
        "body": [
            "<template>",
            "  <div>\n",
            "  </div>",
            "</template>\n",
            "<script>",
            "export default {",
            "}",
            "</script>\n",
            "<style lang=\"stylus\" rel=\"stylesheet/stylus\">",
            "</style>",
            "$2"
        ],
        "description": "Log output to console"
    }
}
```

#### 5 vue组件化开发

- 对于非路由组件，一般放在components文件夹下面，对于路由组件一般放在pages文件夹下面

#### 6 vue-router的使用

- 对于路由组件，使用vue-router进行页面的路由，所以要在router文件夹下面的index.js中进行注册

  ​

#### FooterGuide的开发

- 作用:作页面底部的导航作用

```
FooterGuide.vue
<template>
  <footer class="footer_guide border-1px">
    <a href="javascript:;" class="guide_item" :class="{on: '/msite' === $route.path}" @click="goTo('/msite')">
      <span class="item_icon">
        <i class="iconfont icon-waimai"></i>
      </span>
      <span>外卖</span>
    </a>
    <a href="javascript:;" class="guide_item" :class="{on: '/search' === $route.path}" @click="goTo('/search')">
      <span class="item_icon">
        <i class="iconfont icon-sousuo"></i>
      </span>
      <span>搜索</span>
    </a>
    <a href="javascript:;" class="guide_item" :class="{on: '/order' === $route.path}" @click="goTo('/order')">
      <span class="item_icon">
        <i class="iconfont icon-order1"></i>
      </span>
      <span>订单</span>
    </a>
    <a href="javascript:;" class="guide_item" :class="{on: '/profile' === $route.path}" @click="goTo('/profile')">
      <span class="item_icon">
        <i class="iconfont icon-wode"></i>
      </span>
      <span>我的</span>
    </a>
  </footer>
</template>
```

- 总结：
  - 改变图标的状态，通过的是对class的绑定属性
  - 使用点击事件进行页面的路由

#### HeaderTop的开发

- HeaderTop是一个非路由组件,用于功能页面的最上面的title的展示
  - 会用到slot, 用于传输数据

```
HeaderTop代码:
<header class="header">
    <slot name="left"></slot>
    <span class="header_title">
      <span class="header_title_text ellipsis">{{title}}</span>
    </span>
    <slot name="right"></slot>
</header>

<script>
export default {
    props:{
        title:String
    }
};

使用:
 <HeaderTop title="深圳市龙岗区富璟花园">
      <router-link slot="left" to="/search" class="header_search">
        <i class="iconfont icon-sousuo"></i>
      </router-link>
      <router-link slot="right" to="/login" class="header_login">
        <span class="header_login_text">登录|注册</span>
      </router-link>
 </HeaderTop>
```

#### 使用swipe实现页面的轮播

- 先安装swipe ``npm install swiper``
- 引入和使用swipe

```
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

 mounted() {
    var mySwiper = new Swiper(".swiper-container", {
      autoplay: true,
      loop: true
    });
  },
```

- swipe的官方案例

```
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide">slider1</div>
    <div class="swiper-slide">slider2</div>
    <div class="swiper-slide">slider3</div>
  </div>
</div>
<script>
var mySwiper = new Swiper('.swiper-container', {
	autoplay: true,//可选选项，自动滑动
})

//如果你初始化时没有定义Swiper实例，后面也可以通过Swiper的HTML元素来获取该实例
new Swiper('.swiper-container')
var mySwiper = document.querySelector('.swiper-container').swiper
mySwiper.slideNext();
</script>
```

#### 控制FooterGuide的显示和隐藏

- 在登陆和注册页面，不需要显示FooterGuide组件，可以使用meta元素来进行控制

```
app.vue 中

<FooterGuide v-show="$route.meta.showFooter"></FooterGuide>

在router中

{
  path: '/profile',
  component: Profile,
  meta: { showFooter: true }
},
```

