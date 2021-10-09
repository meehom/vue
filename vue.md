# Vue学习

## 1 初识Vue

### 1.1 Vue 环境的搭建

> 下载Vue.js 和 Vue.min.js 。前者是开发版，会有一些相应的提示，后者是线上版，是上线用的，量级较轻

![image-20211009225033595](https://gitee.com/meehom_liao/typera/raw/master/img/202110092250760.png)

开发版本下载下来是vue.js，生产版本是vue.min.js

> 文件目录的构建：创建一个文件夹，文件夹创建一个目录1_初始vue，另一个目录js，在js文件夹下放入下载的vue.js和vue.min.js，之后创建一个html文件

![image-20211009223749867](https://gitee.com/meehom_liao/typera/raw/master/img/202110092237919.png)

> 初始vue.html相关的代码

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>
  // 这里可以消除warning2
  <script>
    Vue.config.productionTip = false
  </script>
<body>
</body>

</html>
```

这个时候发现浏览器后面有两个warning，warning1是需要安装dev工具，warning2是提示不提示相关信息

warning1：通过在谷歌商店下载vue js devtools 插件进行解决

warning2：通过修改该vue.config.productionTip进行解决



### 1.2 Vue 实现hello meehom

> 指定页面图标: favicon.ico,在根目录下放置一个图标

![image-20211009231534841](https://gitee.com/meehom_liao/typera/raw/master/img/202110092315932.png)

>创建Vue实例

```html
	// 创建Vue实例
    const x = new Vue({
      el: '#root', // el用于指定Vue为哪个实例，值是css选择器
      data: {
        name: 'meehom'
      }
    })
```

**el：用来绑定容器**

**data：用来存储数据**

>创建容器

```html
<div id="root">
    <li>hello, {{name}}</li>
</div>
```

**{{}} 里面可以直接绑定data中数据**

>完整代码

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8">
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <div id="root">
    <li>hello, {{name}}</li>
  </div>
  <script>
    Vue.config.productionTip = false

    // 创建Vue实例
    const x = new Vue({
      el: '#root', // el用于指定Vue为哪个实例，值是css选择器
      data: {
        name: 'meehom'
      }
    })
  </script>

</body>

</html>
```

