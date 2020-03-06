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
  - ​

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
- ​