

# vue2学习笔记

# Vue.js 目录结构

### 目录解析

![img](https://www.runoob.com/wp-content/uploads/2017/01/B6E593E3-F284-4C58-A610-94C6ACDAD485.jpg)

| 目录/文件    | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| build        | 项目构建(webpack)相关代码                                    |
| config       | 配置目录，包括端口号等。我们初学可以使用默认的。             |
| node_modules | ==npm 加载的项目依赖模块==                                   |
| src          | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：==assets: 放置一些图片==，如logo等。==components: 目录里面放了一个组件文件==，可以不用。A==pp.vue: 项目入口文件，==我们也可以直接将组件写这里，而不使用 components 目录。==main.js: 项目的核心文件==。 |
| static       | ==静态资源目录==，如图片、字体等。                           |
| test         | 初始测试目录，可删除                                         |
| .xxxx文件    | 这些是一些配置文件，包括语法配置，git配置等。                |
| index.html   | ==首页入口文件，你可以添加一些 meta 信息或统计代码啥的==。   |
| package.json | ==项目配置文件。==                                           |
| README.md    | ==项目的说明文档，markdown 格式==                            |





Evan You

Taylor otwell

1.声明式编码

==学习vue之前要掌握JavaScript基础知识==

原型和原型链非常重要

![image-20210819103946621](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210819103946621.png)



==官网最重要==

- 教程

- API——方法

![image-20210819104812060](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210819104812060.png)

# 1 初识Vue

​        1.想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象；

​        2.root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法；

​        3.root容器里的代码被称为【Vue模板】；

​        4.Vue实例和容器是一一对应的；  数据是动态的，不用再次更新

​        5.真实开发中只有一个Vue实例，并且会配合着组件一起使用；

​        6.=={{xxx}}中的xxx要写js表达式==，且xxx可以自动读取到data中的所有属性；

​        7.一旦data中的数据发生改变，那么页面中用到该数据的地方也会自动更新；



​        注意区分：js表达式 和 js代码(语句)

​            1.表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方：

​                  (1). a

​                  (2). a+b

​                  (3). demo(1)  函数调用表达式

​                  (4). x === y ? 'a' : 'b'

​            2.js代码(语句)

​                  (1). if(){}

​                  (2). for(){}



# 2 Vue模板语法有2大类：

​          1.插值语法：

​              功能：用于解析==标签体内容==。

​              写法：{{xxx}}，xxx是js表达式，且可以直接读取到data中的所有属性。

​          2.指令语法：

​              功能：用于==解析标签==（包括：标签属性、标签体内容、绑定事件.....）。

​              举例：v-bind:href="xxx" 或 简写为 :href="xxx"，xxx同样要写js表达式，

​                   且可以直接读取到data中的所有属性。

​              备注：Vue中有很多的指令，且形式都是：v-????，此处我们只是拿v-bind举个例子。

## 我们学过的指令：

​            v-bind : 单向绑定解析表达式, 可简写为 :xxx

​            v-model : 双向数据绑定

​            v-for  : 遍历数组/对象/字符串

​            v-on  : 绑定事件监听, 可简写为@

​            v-if    : 条件渲染（动态控制节点是否存存在）

​            v-else : 条件渲染（动态控制节点是否存存在）

​            v-show : 条件渲染 (动态控制节点是否展示)

v-text指令：

​            1.作用：向其所在的节点中渲染文本内容。

​            2.与插值语法的区别：v-text会替换掉节点中的内容，{{xx}}则不会。

 v-html指令：

​            1.作用：向指定节点中渲染包含html结构的内容。

​            2.与插值语法的区别：

​                  (1).v-html会替换掉节点中所有的内容，{{xx}}则不会。

​                  (2).v-html可以识别html结构。

​            3.严重注意：v-html有安全性问题！！！！

​                  (1).在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。

​                  (2).一定要在可信的内容上使用v-html，永不要用在用户提交的内容上！

# 3 Vue中有2种数据绑定的方式：

​          ==1.单向绑定(v-bind)：数据只能从data流向页面。==      

​          ==2.双向绑定(v-model)：数据不仅能从data流向页面，还可以从页面流向data。==

​            备注：

​                1.双向绑定<u>一般都应用在表单类元素</u>【输入类元素，和用户产生交互】上（如：input、select等）

​                2.==v-model:value 可以简写为 v-model==，因为v-model默认收集的就是value值。

# 4 data与el的2种写法

​          1.el有2种写法

​                  (1).new Vue时候配置el属性。

​                  (2).先创建Vue实例，随后再通过vm.$mount('#root')指定el的值。

​          2.data有2种写法

​                  (1).对象式

​                  (2).函数式

​                  如何选择：目前哪种写法都可以，以后学习到组件时，data必须使用函数式，否则会报错。

​          3.一个重要的原则：

​                  由Vue管理的函数，一定不要写箭头函数，一旦写了箭头函数，this就不再是Vue实例了。

# 5 MVVM模型



​            \1. M：模型(Model) ：data中的数据

​            \2. V：视图(View) ：模板代码

​            \3. VM：视图模型(ViewModel)：Vue实例

​      观察发现：

​            1.data中所有的属性，最后都出现在了vm身上。

​            2.vm身上所有的属性 及 Vue原型上所有属性，在Vue模板中都可以直接使用。



1.Vue中的数据代理：

​              通过vm对象来代理data对象中属性的操作（读/写）

2.Vue中数据代理的好处：

​              更加方便的操作data中的数据

3.基本原理：

​              通过Object.defineProperty()把data对象中所有属性添加到vm上。

​              为每一个添加到vm上的属性，都指定一个getter/setter。

​              在getter/setter内部去操作（读/写）data中对应的属性。



### Html

使用 v-html 指令用于输出 html 代码：

==用在标签中，而不是标签的值中==

~~~html
<div id="app">
    <div v-html="message"></div>
</div>
~~~

## 属性

HTML 属性中的值应使用 ==v-bind 指令==。

以下实例判断 use 的值，如果为 true 使用 class1 类的样式，否则不使用该类：

~~~html
 <div v-bind:class="{'class1': use}">
    v-bind:class 指令
  </div>
~~~

### 表达式

Vue.js 都提供了完全的 JavaScript 表达式支持。

## 指令

指令是带有 v- 前缀的特殊属性。

指令用于在表达式的值改变时，将某些行为应用到 DOM 上。如下例子：

> 指令都是写在标签中，而不是作为标签的内容

### 参数

参数在指令后以冒号指明。例如， v-bind 指令被用来响应地更新 HTML 属性：

### 修饰符

修饰符是以半角句号 **.** 指明的特殊后缀，==用于指出一个指令应该以特殊方式绑定==。例如，**.prevent** 修饰符告诉 **v-on** 指令对于触发的事件调用 **event.preventDefault()**：

```
<form v-on:submit.prevent="onSubmit"></form>
```

------

## 用户输入

在 input 输入框中我们可以使用 v-model 指令来实现双向数据绑定：

**v-model** 指令用来在 ==input、select、textarea、checkbox、radio 等表单控件元素==上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值。

按钮的事件我们可以使用 v-on 监听事件，并对用户的输入进行响应。

~~~html


<body>
    <div id="app">
        <p>{{ message }}</p>
        <button v-on:click="reverseMessage">反转字符串</button>
    </div>
        
    <script>
    new Vue({
      el: '#app',
      data: {
        message: 'Runoob!'
      },
      methods: {
        reverseMessage: function () {
            console.log(this)
           // this是vue对象，其中包含vue对象的所有数据和方法 
          this.message = this.message.split('').reverse().join('')
        }
      }
    })
    </script>
    </body>
    </html>
~~~

## 过滤器

Vue.js 允许你自定义过滤器，被用作一些常见的文本格式化。由"管道符"指示, 格式如下：

```
<!-- 在两个大括号中 -->
{{ message | capitalize }}

<!-- 在 v-bind 指令中 -->
<div v-bind:id="rawId | formatId"></div>
```

过滤器函数接受表达式的值作为第一个参数。

过滤器可以串联：

```
{{ message | filterA | filterB }}
```

过滤器是 JavaScript 函数，因此可以接受参数：

```
{{ message | filterA('arg1', arg2) }}
```

这里，message 是第一个参数，字符串 'arg1' 将传给过滤器作为第二个参数， arg2 表达式的值将被求值然后传给过滤器作为第三个参数。

------

## 缩写

### v-bind 缩写

Vue.js 为两个最为常用的指令提供了特别的缩写：

```
<!-- 完整语法 -->
<a v-bind:href="url"></a>
<!-- 缩写 -->
<a :href="url"></a>
```

### v-on 缩写

```
<!-- 完整语法 -->
<a v-on:click="doSomething"></a>
<!-- 缩写 -->
<a @click="doSomething"></a>
```

```
<!-- Handlebars 模板 -->
{{#if ok}}
  <h1>Yes</h1>
{{/if}}
```

# 条件语句

```
<!-- Handlebars 模板 -->
{{#if ok}}
  <h1>Yes</h1>
{{/if}}
```

### v-if



### v-else



### v-else-if

*v-else 、v-else-if 必须跟在 v-if 或者 v-else-if之后。*

### v-show

我们也可以使用 v-show 指令来根据条件展示元素：





- 文本
- html
- 属性
- 表达式

指令

- 参数
- 修饰符

用户输入

过滤器

缩写

# 路由

1.路由嵌套很少到七层的；

![image-20210824104721058](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210824104721058.png)



![image-20210824104816311](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210824104816311.png)



多页面应用

单页面应用——体验更好

# 7 事件处理

Vue中的事件修饰符：【记住前三个】

​            ==1.prevent：阻止默认事件（常用）；==

​            ==2.stop：阻止事件冒泡（常用）；==

​            ==3.once：事件只触发一次（常用）；==

​            4.capture：使用事件的捕获模式；

​            5.self：只有event.target是当前操作的元素时才触发事件；

​            6.passive：事件的默认行为立即执行，无需等待事件回调执行完毕；

​      滚动

- @scroll    滚动条触发，不是滚轮
- @whell    鼠标滚轮触发，不是滚动条

### 键盘事件



1.Vue中常用的按键别名：

​              回车 => enter

​              删除 => delete (捕获“删除”和“退格”键)

​              退出 => esc

​              空格 => space

​              换行 => tab (特殊，必须配合keydown去使用)

​              上 => up

​              下 => down

​              左 => left

​              右 => right

 2.Vue未提供别名的按键，可以使用按键原始的key值去绑定，但注意要转为kebab-case（短横线命名）

3.系统修饰键（用法特殊）：ctrl、alt、shift、meta

​              (1).配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发。

​              (2).配合keydown使用：正常触发事件。

4.也可以使用keyCode去指定具体的按键（不推荐） 【编码不推荐】

5.Vue.config.keyCodes.自定义键名 = 键码，可以去定制按键别名

![image-20210822101750587](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210822101750587.png)

tab键可以改变焦点，失去对当前元素的焦点

# 8 计算属性

​          1.定义：==要用的属性不存在==，要通过==已有属性==计算得来。

​          2.原理：底层借助了Objcet.defineproperty方法提供的getter和setter。

​          3.get函数什么时候执行？

​                (1).初次读取时会执行一次。

​                (2).当依赖的数据发生改变时会被再次调用。

​          4.优势：与methods实现相比，内部有==缓存机制==（复用），效率更高，==调试方便。==

​          5.备注：

​              ==1.计算属性最终会出现在vm上，直接读取使用即可。==

​              2.如果计算属性要被修改，那必须写set函数去响应修改，==且set中要引起计算时依赖的数据发生改变。==【真正进行改变】

data：是属性

computed：是计算属性

~~~vue
computed:{
		fullName:{
//get有什么作用？当有人读取fullName时，get就会被调用，且返回值就作为fullName的值
//get什么时候调用？1.初次读取fullName时。2.所依赖的数据发生变化时。
		get(){
		console.log('get被调用了')
		// console.log(this) //此处的this是vm
  		return this.firstName + '-' + this.lastName
					},
//set什么时候调用? 当fullName被修改时。
					set(value){
						console.log('set',value)
						const arr = value.split('-')
						this.firstName = arr[0]
						this.lastName = arr[1]
					}
				}
~~~

- 只读不改

~~~vue
//简写
fullName(){
		console.log('get被调用了')
		return this.firstName + '-' + this.lastName
		 }
~~~

# 9 监视属性

​        监视属性watch：

​          1.当被监视的属性变化时, 回调函数自动调用, 进行相关操作

​          2.监视的属性必须存在，才能进行监视！！

​          3.监视的两种写法：

​              (1).new Vue时传入watch配置

​              (2).通过vm.$watch监视

### 深度监视



​            (1).Vue中的watch==默认不监测对象内部值的改变（一层）==。

​            (2).配置==deep:true==可以监测对象内部值改变（多层）。

​        备注：

​            (1).Vue==自身可以监测==对象内部值的改变，但Vue提供的watch默认不可以！

​            (2).使用watch时根据数据的具体结构，决定是否采用深度监视。

​        computed和watch之间的区别：

​            1.computed能完成的功能，watch都可以完成。

​            2.watch能完成的功能，computed不一定能完成，例如：watch可以进行异步操作。



~~~vue
 // 已经明确监视对象
watch:{
	isHot:{
		immediate:true, //初始化时让handler调用一下
		//handler什么时候调用？当isHot发生改变时。
		handler(newValue,oldValue){
		console.log('isHot被修改了',newValue,oldValue)
					}
				}
			} 
~~~

~~~vue
// 创建vue对象时不知道监视对象
vm.$watch('isHot',{
	immediate:true, //初始化时让handler调用一下
	//handler什么时候调用？当isHot发生改变时。
	handler(newValue,oldValue){
	console.log('isHot被修改了',newValue,oldValue)
			}
~~~

~~~vue
//监视多级结构中所有属性的变化
				numbers:{
					deep:true,
					handler(){
					console.log('numbers改变了')
					}
				}
~~~

~~~vue
watch:{
	isHot:{
	// immediate:true, //初始化时让handler调用一下
	// deep:true,//深度监视
		handler(newValue,oldValue){
		console.log('isHot被修改了',newValue,oldValue)}
			}, 
//简写
	isHot(newValue,oldValue){
		console.log('isHot被修改了',newValue,oldValue,this)} 
			
~~~

~~~vue
//正常写法
vm.$watch('isHot',{
	immediate:true, //初始化时让handler调用一下
	deep:true,//深度监视
	handler(newValue,oldValue){
	console.log('isHot被修改了',newValue,oldValue)
			}
		}) 

//简写
vm.$watch('isHot',(newValue,oldValue)=>{
	console.log('isHot被修改了',newValue,oldValue,this)
		}) 
~~~

###  computed和watch之间的区别

​            ==1.computed能完成的功能，watch都可以完成。==     【计算属性更加简单】

​            2.watch能完成的功能，computed不一定能完成，例如：==watch可以进行异步操作。==

### 两个重要的小原则

​              ==1.所被Vue管理的函数，最好写成普通函数，这样this的指向才是vm 或 组件实例对象。==

​              ==2.所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数等、Promise的回调函数），最好写成箭头函数，==

​                这样this的指向才是vm 或 组件实例对象。

~~~vue
watch:{
	firstName(val){
// 定时器，不是vue不是管理的，而是系统管理的
		setTimeout(()=>{
			console.log(this)
			this.fullName = val + '-' + this.lastName
					},1000);
				},
	lastName(val){
		this.fullName = this.firstName + '-' + val}
~~~

# 10 绑定样式

​	【vue管理动态内容】

1. class样式

​                写法:class="xxx" xxx可以是字符串、对象、数组。

- ==字符串写法适用于：类名不确定，要动态获取。==

​      <!-- 绑定class样式--字符串写法，适用于：样式的类名不确定，需要动态指定 -->

- 对象写法适用于：要绑定多个样式，个数不确定，名字也不确定。

​      <!-- 绑定class样式--数组写法，适用于：要绑定的样式个数不确定、名字也不确定 -->

- 数组写法适用于：要绑定多个样式，个数确定，名字也确定，但不确定用不用。

​      <!-- 绑定class样式--对象写法，适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用 -->

2. style样式

   对象写法

- :style="{==fontSize==: xxx}"其中xxx是动态值。【其中的key不能乱写，要写style中的样式对象】

  数组写法

​                :style="[a,b]"其中a、b是样式对象。

# 11 条件渲染

​              1.v-if

​                    写法：

​                        (1).v-if="表达式" 

​                        (2).v-else-if="表达式"

​                        (3).v-else="表达式"

​                    适用于：==切换频率较低==的场景。

​                    特点：不展示的DOM元素==直接被移除==。

​                    注意：v-if可以和:v-else-if、v-else一起使用，但要求结构不能被“打断”。

​              2.v-show

​                    写法：v-show="表达式"      【底层dispaly:none】

​                    适用于：==切换频率较高==的场景。

​                    特点：==不展示的DOM元素未被移除==，仅仅是使用样式隐藏掉

​              3.备注：使用v-if的时，元素可能无法获取到，而使用v-show一定可以获取到。

# 12 列表渲染！！！

- vue中对象用{ }

- 使用遍历，要使用key来标识，key不能相同

## v-for指令

​            1.用于展示列表数据

​            2.语法：v-for="(item, index) in xxx" :key="yyy"

​            3.可遍历：==数组==、对象、字符串（用的很少）、指定次数（用的很少）

​        面试题：react、vue中的key有什么作用？（key的内部原理）

​            

1. 虚拟DOM中key的作用：

​                    key是虚拟DOM对象的标识，当数据发生变化时，==Vue会根据【新数据】生成【新的虚拟DOM】,== 

​                    随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下：

​            2.对比规则：

​                  (1).旧虚拟DOM中找到了与新虚拟DOM相同的key：

​                        ①.若虚拟DOM中内容没变, ==直接使用之前的真实DOM！==

​                        ②.若虚拟DOM中内容变了, ==则生成新的真实DOM，随后替换掉页面中之前的真实DOM。==

​                  (2).旧虚拟DOM中未找到与新虚拟DOM相同的key

​                        ==创建新的真实DOM，随后渲染到到页面。==    

3. 用index作为key可能会引发的问题：

​                      \1. 若对数据进行：逆序添加、逆序删除等==破坏顺序操作==:

​                              会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。

​                      \2. 如果==结构中还包含输入类的DOM==：

​                              会产生错误DOM更新 ==> 界面有问题。

4. 开发中如何选择key?:

​                      1.==最好使用每条数据的唯一标识==作为key, 比如id、手机号、身份证号、学号等唯一值。

​                      2.如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，==仅用于渲染列表用于展示，==

​                        ==使用index作为key是没有问题的。==

​     

## Vue监视数据的原理

​        \1. vue会监视data中所有层次的数据。

​        \2. 如何监测对象中的数据？

​                通过setter实现监视，且要在new Vue时就传入要监测的数据。

​                  (1).对象中后追加的属性，Vue默认不做响应式处理

​                  (2).如需给后添加的属性做响应式，请使用如下API：

​                          Vue.set(target，propertyName/index，value) 或 

​                          vm.$set(target，propertyName/index，value)

​        \3. 如何监测数组中的数据？

​                  通过包裹数组更新元素的方法实现，本质就是做了两件事：

​                    (1).调用原生对应的方法对数组进行更新。

​                    (2).重新解析模板，进而更新页面。

​        4.在Vue修改数组中的某个元素一定要用如下方法：

​              1.使用这些API:push()、pop()、shift()、unshift()、splice()、sort()、reverse()

​              2.Vue.set() 或 vm.$set()

​              特别注意：Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象 添加属性！！！

- 原数组不能改变！

# 13 收集表单数据

​      收集表单数据：

​          若：<input type="text"/>，则v-model收集的是value值，用户输入的就是value值。

​          若：<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值。

​          若：<input type="checkbox"/>

​              1.没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​              2.配置input的value属性:

​                  (1)v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）

​                  (2)v-model的初始值是数组，那么收集的的就是value组成的数组

​          备注：v-model的三个修饰符：

​                  lazy：失去焦点再收集数据

​                  number：输入字符串转为有效的数字

​                  trim：输入首尾空格过滤

# 过滤器

​        定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。

​        语法：

​            1.注册过滤器：Vue.filter(name,callback) 或 new Vue{filters:{}}

​            2.使用过滤器：{{ xxx | 过滤器名}} 或 v-bind:属性 = "xxx | 过滤器名"

​        备注：

​            1.过滤器也可以接收额外参数、多个过滤器也可以串联

​            2.并没有改变原本的数据, 是产生新的对应的数据

bootcdn.cn

moment.js

day.js

# 16 自定义指令

​        需求1：定义一个v-big指令，和v-text功能类似，但会把绑定的数值放大10倍。

​        需求2：定义一个v-fbind指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。

​        自定义指令总结：

​            一、定义语法：

​                  (1).局部指令：  【一个vue实例】

​     new Vue({                                                      new Vue({

​      directive==s==:{指令名:配置对象}  或               directive==s=={指令名:回调函数}

​                        })                                                                  })

​                  (2).全局指令：

​                          Vue.directive(指令名,配置对象) 或  Vue.directive(指令名,回调函数)

​            二、配置对象中常用的3个回调：

​                  (1).bind：指令与元素成功绑定时调用。

​                  (2).inserted：指令所在元素被插入页面时调用。

​                  (3).update：指令所在模板结构被重新解析时调用。

​            三、备注：

​                  1.指令定义时不加v-，==但使用时要加v-==；

​                  2.指令名如果是多个单词，要使用==kebab-case==【单词之间连字符连接】命名方式，不要用camelCase命名。

- ==所有指令相关的回调this都是Windows，而不是对象==

# 17 生命周期

【生命周期！！特别重要】

​            1.又名：生命周期回调函数、生命周期函数、**生命周期钩子**。【等着vue调用】

​            2.是什么：Vue在==关键时刻帮我们调用的==一些特殊名称的函数。

​            3.==生命周期函数的名字不可更改==，但函数的具体内容是程序员根据需求编写的。

​            4.生命周期函数中的==this指向是vm==   或    组件实例对象。

常用的生命周期钩子：

​            1.mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等==【初始化操作】。==

- Vue完成模板的解析并把==初始的==真实==DOM元素放入页面==后（挂载完毕）调用mounted   【第一次将东西放进页面，之后就是更新】

​            2.beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

~~~vue
// 动态样式用冒号
<h2 :style="{opacity}">欢迎学习Vue</h2>
~~~

~~~vue
		//通过外部的定时器实现（不推荐）
		/* setInterval(() => {
			vm.opacity -= 0.01
			if(vm.opacity <= 0) vm.opacity = 1
		},16) */
~~~

undefined不显示在页面上

改vue中的data数据，就会重新解析模板

![生命周期](C:\Users\Carrie_Lee\Desktop\追踪溯源\资料（含课件）\02_原理图\生命周期.png)

## 挂载流程

1.初始化事件和生命周期

生命周期函数有哪些，何时调用？

事件修饰符（一次性修饰符）如何处理？

data:{n:1}    此时vm还没收到，vm还没有_data

==beforeCreate==

无法通过vm访问到data中的数据、methods中的方法

2.初始化数据监测和数据代理

数据监测

![image-20211008103458945](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008103458945.png)

数据代理

![image-20211008103546710](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008103546710.png)

==created==

可以通过vm访问到data中的数据、methods中配置的方法

option指的是vm中的配置项

![image-20211008103811738](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008103811738.png)

绿色是outerHTML，

==beforeMount==



![image-20211008104450922](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008104450922.png)

将内存中的虚拟DOM转为真实的DOM插入页面

真实DOM结构保存在vm.$el身上

![image-20211008112410719](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008112410719.png)

### vm.$mount( [elementOrSelector\] )](https://cn.vuejs.org/v2/api/#vm-mount)



==mounted==     【重要的钩子】

一上来要写的内容全部写在这里 【初始化的工作】

至此vue初始化过程结束，在此阶段：开启定时器、发送网络请求、订阅消息、绑定自定义事件等初始化操作

走没走过的选择：

![image-20211008110212580](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008110212580.png)

template配置

![image-20211008111211122](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008111211122.png)

div配置

![image-20211008111417074](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008111417074.png)

## 更新流程

![image-20211008111715249](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008111715249.png)

当data中的数据发生改变时，

==beforeUpdate==

数据是新的，但是页面是旧的，此时数据和页面没有保持同步

![image-20211008113012871](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008113012871.png)

生成新的虚拟DOM，和旧的虚拟DOM 进行不比较，最终完成页面更新，model--view的更新

==updated==

数据和页面保持同步了

## 销毁流程

![image-20211008113547451](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20211008113547451.png)

destroy销毁vm，vm的工作成果还在

### [vm.$destroy()](https://cn.vuejs.org/v2/api/#vm-destroy)

**用法**：

完全销毁一个实例。清理它与其它实例的连接，**解绑它的全部指令**及**事件监听器**【指的是自定义事件，点击事件是原生的DOM 事件】。

在大多数场景中你不应该调用这个方法。最好使用 `v-if` 和 `v-for` 指令以数据驱动的方式控制子组件的生命周期。

触发 `beforeDestroy` 和 `destroyed` 的钩子。

开发工具中vue中没有内容了

~~~html
<h2 v-text='n'> </h2>

<button @click="add">点我n+1</button>
<button @click="bye">点我销毁vm</button  // 原生DOM事件并没有被销毁
~~~



==beforeDestroy==    【重要的钩子】 

【收尾的工作】

vm中所有的data、methods、指令等，都处于可用状态，马上要执行销毁过程，对所有数据的更新不会触发更新了【在此处不要操作数据！！】，做一些收尾工作

==destroyed==

移除vm所有的监视、子组件和事件监听器【自定义事件】

【这个钩子用的最少！！！】









```vue
		beforeCreate() {
			console.log('beforeCreate')
		},
		created() {
			console.log('created')
		},
		beforeMount() {
			console.log('beforeMount')
		},
		// 挂载完毕
		// 大部分是挂载函数
		mounted() {
			console.log('mounted')
		},
		// 更新非常简单
		beforeUpdate() {
			console.log('beforeUpdate')
		},
		updated() {
			console.log('updated')
		},
		// 可以调用数据，但对数据不进行更新
		// 只进行收尾工作，对数据不进行相关操作
		beforeDestroy() {
			console.log('beforeDestroy')
		},
		destroyed() {
			console.log('destroyed')
		},
```

- ==面试会问？==

​        关于销毁Vue实例

​            1.销毁后借助Vue开发者工具看不到任何信息。

​            2.销毁后自定义事件会失效，==但原生DOM事件依然有效==。

​            3.==一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。==

- js对小数的处理欠缺，不擅长

- 红色是生命周期函数

- <template>不能作为根元素，



# 18 非单文件组件（封装）

官网视频

样式 结构 交互

![image-20210823142101301](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823142101301.png)



![image-20210823142220321](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823142220321.png)

54课，仔细看

## Vue中使用组件的三大步骤

​          一、定义组件(创建组件)

​          二、注册组件

​          三、使用组件(写组件标签)



​      一、如何定义一个组件？

​            使用==Vue.extend==(options)创建，其中options和new Vue(options)时传入的那个options几乎一样，但也有点区别；

​            区别如下：

​                1.el不要写，为什么？ ——— 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。

​                2.data必须写成函数，为什么？ ———— 避免组件被复用时，数据存在引用关系。

​            备注：使用template可以配置组件结构。

​      二、如何注册组件？

​              1.局部注册：靠new Vue的时候传入==components==选项

​              2.全局注册：靠==Vue.componen==t('组件名',组件)

​      三、编写组件标签：

​              <school></school>

​     

- 几个注意点：

​          1.关于==组件名:==

​                一个单词组成：

​                      ==第一种写法(首字母小写)：school==

​                      第二种写法(首字母大写)：School

​                多个单词组成：

​                      ==第一种写法(kebab-case命名)：my-school==

​                      第二种写法(CamelCase命名)：MySchool (需要Vue脚手架支持)

​                备注：

​                    (1).组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。

​                    (2).可以使用name配置项指定组件==在开发者工具中呈现的名字==。

​          2.关于组件标签:

​                第一种写法：<school></school>

​                第二种写法：<school/>

​                备注：不用使用脚手架时【必须webpack配置环境，直接引用vue.js，不能】，<school/>会导致后续组件不能渲染。

​          3.一个简写方式：

​                const school = ==Vue.extend==(options) 可简写为：const school = options

![image-20210823161547899](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823161547899.png)

​      关于VueComponent：

​            1.school==组件本质==是一个名为==VueComponent的构造函数==，且不是程序员定义的，是Vue.extend生成的。

​            2.我们只需要写<school/>或<school></school>，Vue解析时会帮我们创建school组件的==实例对象==，

​              即Vue帮我们执行的：new VueComponent(options)。

​            3.特别注意：==每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！==

​            4.关于this指向：

​                (1).组件配置中：

​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【VueComponent实例对象】。

​                (2).new Vue(options)配置中：

​                      data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。

​            5.==VueComponent的实例对象，以后简称vc==（也可称之为：组件实例对象）。

​              Vue的实例对象，以后简称vm。

![image-20210823163155088](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823163155088.png)

![image-20210823163628571](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823163628571.png)

![image-20210823163722145](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823163722145.png)

​        1.一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype

​        2.为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的==属性、方法。==

![image-20210823164610837](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823164610837.png)

![image-20210823171210197](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210823171210197.png)

- 样式不能包括在组件中，要单拎出来

# 19 单文件组件

vue不是HTML文件，包括

- HTML， <template>  组件的结构
- css，  <style>  组件样式
- js    <script> 组件交互相关的代码

main.js文件：【入口文件】

- 创建vue实例，

App.vue文件：汇总所有组件

index.html文件：【页面】

- 引入main.js文件

组件划分按照功能；名字语义化一点；组件起名合理，组件是否拆分合理







组件之间的通信非常重要！！！！

![image-20210825092152858](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825092152858.png)

.gitignore文件：

babel.config.js文件：重要，babel的控制文件，ES6->ES5，进行相关配置，直接使用官网的配置即可，

两个package文件：

![image-20210825092558238](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825092558238.png)

1.配置好服务器；

2.打包文件，所有功能已经写完，最后的一次编译，将HTML和vue文件转换成HTML，css，js

3.lint将js和.vue文件进行语法检查，很少用

4.记录包的URL，很快下载

![image-20210825093054960](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825093054960.png)

npm run serve命令执行后，就去运行main.js文件；

![image-20210825094051139](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825094051139.png)

assets文件：存放静态资源，如图片、视频等

components文件夹：存放组件，除去pp

![image-20210825095129164](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825095129164.png)

public/index.html是整个应用的界面

![image-20210825101443917](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825101443917.png)

![image-20210825102056598](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825102056598.png)

引入残缺版的vue：

1.残缺的vue不能写元素，那么使用render来创建元素，写模板render(createElement) {

​    return createElement('h1', '你好啊')

module是残缺的vue，完整版在dist/vue.js

2.vue两部分

- 核心

- 模板解析器，文件很大【精简版，打包时去除，runtime.js文件】

![image-20210825105636939](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825105636939.png)

## 脚手架的默认配置

vue inspect > output.js

![image-20210825110539986](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210825110539986.png)

红色不要改，但是可以改

vue cli官网配置文件中写的配置可以改动

## ref属性

给哪个元素绑定==ref==，vue就收集哪个元素的==组件实例对象==





# 全局事件总线？？？

任意组件间通信；这是程序员的经验所得

x就是总线bus，vm和vc都能看到$bus；总线不能被同时占用，不能发生冲突

![image-20210824091305856](C:\Users\Carrie_Lee\AppData\Roaming\Typora\typora-user-images\image-20210824091305856.png)

$on,$off,$emit在vue的原型对象上

