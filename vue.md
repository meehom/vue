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

### 1.3 Vue 的模板语法

>插值语法

```html
<h1>你好 {{name}}</h1>
```

对于标签内的内容，可以用插值语法进行赋值

>指令语法

```html
<a v-bind:href="url">点我跳转到{{school.name}}</a>
<a :href="url">点我跳转到{{school.name}}</a>
```

对于标签里面的属性，可以通过指令语法进行赋值

>示例代码

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
    <h1>插值语法</h1>
    <h1>你好 {{name}}</h1>
    <hr />
    <h1>指令语法</h1>
    <a v-bind:href="url">点我跳转到{{school.name}}</a>
    <a :href="url">点我跳转到{{school.name}}</a>

  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        name: 'jack',
        url: 'http://www.baidu.com',
        school: {
          name: '百度'
        }

      }
    })


  </script>

</body>

</html>
```

### 1.4 单项绑定和双向绑定

**1.4.1单项绑定**

>单项绑定是指Vue中的data显示到页面上，页面上的数据改变，不会影响Vue实例的对象。通常通过v-bind实现

```html
 <h1>单向绑定</h1><input type="text" :value="value" /><br />
```

**1.4.2 双向绑定**

> 双向绑定是指Vue中的data可以被DOM中的数据影响，然后data又可以回显到DOM中去。通常通过v-model实现，v-model:value通常简写为v-model

```html
<h1>双向绑定</h1><input type="text" v-model:value="value" />
```

**1.4.3 代码展示**

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
    <h1>单向绑定</h1><input type="text" :value="value" /><br />
    <h1>双向绑定</h1><input type="text" v-model="value" />
  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        value: 'meehom'
      }
    })
  </script>

</body>

</html>
```

### 1.5 el与data的两种写法

**el的两种写法**

>写法1：直接创建实例的时候绑定el

```html
new Vue({
      	el: '#root', // el的第一种写法
      	data: {
      	name: 'meehom' // data 的第一种写法，对象式
      	}
})
```

> 写法2：创建实例后在给el赋值

```html
var v = new Vue({
      	data: {
      	name: 'meehom' // data 的第一种写法，对象式
      	}
})
v.$mount = '#root'
```



**data的两种写法**

> 写法1：对象式

```html
new Vue({
      	el: '#root', // el的第一种写法
      	data: {
      	name: 'meehom' // data 的第一种写法，对象式
      	}
})
```

> 写法2：函数式

```html
new Vue({
      	el: '#root', // el的第一种写法
      	data: function(){  // 可简写为data(){}
			return {
      			name: 'meehom' // data 的第二种写法，函数式
      			}
		}
})
```



### 1.6 MVVM模型

![image-20211010152102272](https://gitee.com/meehom_liao/typera/raw/master/img/202110101521434.png)

>M：对应这就是data里面的数据，V：对应的就是页面，VM对应的就是Vue实例

![image-20211010152431035](https://gitee.com/meehom_liao/typera/raw/master/img/202110101524128.png)

数据的流向就是M-->VM-->V，V-->VM-->M



### 1.7 数据代理

> Object.defineProperty 可以给对象增加属性，和修改属性

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
</head>

<body>
  <script type="text/javascript">
    let number = 20
    let person = {
      name: '张三',
      sex: '男',
    }
    Object.defineProperty(person, 'age', {
      // value: 18,
      // enumerable: true,
      // writable: true,
      // configurable: true,

      get() {
        return number
      },

      set(value) {
        number = value
      }
    })
    console.log(person)
  </script>
</body>

</html>
```

>何为数据代理：通过一个对象代理另外一个对象中的属性的操作

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <script>
    Vue.config.productionTip = false
    // 通过一个对象代理另外一个对象中的属性的操作
    let obj = { x: 100 }
    let obj2 = { y: 200 }
    Object.defineProperty(obj2, 'x', {
      get() {
        return obj.x
      },
      set(value) {
        obj.x = value
      }
    })

  </script>
</body>

</html>
```

### 1.8 事件处理

> 简单事件的绑定 v-on:click = 'fun1', 可以简写为@click, 传参可以通过()进行传参，默认传递$event

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <div id="root">
    <h2>欢迎来到{{name}}学习</h2>
    <button v-on:click="showInfo1">点我提示信息(不传参)</button>
    <button @click="showInfo2(66,$event)">点我提示信息(传参)</button>
  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        name: 'meehom学堂'
      },
      methods: {
        showInfo1() {
          alert("你好1")
        },
        showInfo2(data, event) {
          console.log(data)
          console.log(event)
          alert("你好2")
        }
      }
    })
  </script>
</body>

</html>
```

>键盘事件：可以利用@keyup进行绑定

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <div id="root">
    <h2>欢迎来到{{name}}学习</h2>
    <input type="text" placeholder="按下回车提示键入" @keyup.enter='showInfo' />
  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        name: 'meehom学院'
      },
      methods: {
        showInfo(e) {
          console.log(e.target.value)
        }
      }
    })
  </script>
</body>

</html>
```



### 1.9 计算属性

**1.9.1利用插值语法计算属性**

> 使用v-model来实现数据的双向绑定

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <div id="root">
    姓:<input type="text" v-model="firstName" /><br />
    名:<input type="text" v-model="lastName" /><br />
    全名：<span>{{firstName}}-{{lastName}}</span>
  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        firstName: '张',
        lastName: '三',
      }
    })
  </script>
</body>

</html>
```

**1.9.2利用method来实现计算属性**

> method中可以用this指定Vue实例，来访问data

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Document</title>
  <script type="text/javascript" src="../js/vue.js"></script>
</head>

<body>
  <div id="root">
    姓:<input type="text" v-model="firstName" /><br />
    名:<input type="text" v-model="lastName" /><br />
    全名：<span>{{fullName()}}</span>
  </div>
  <script>
    Vue.config.productionTip = false
    new Vue({
      el: '#root',
      data: {
        firstName: '张',
        lastName: '三',
      },
      methods: {
        fullName() {
          return this.firstName + '-' + this.lastName
        }
      }
    })
  </script>
</body>

</html>
```

