# -
基础札记
5语义化
(1)html 语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析；即使在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的;
(2)利用seo
(3)便于阅读理解

标准模式和怪癖模式
（1）盒模型：在 W3C 标准中，如果设置一个元素的宽度和高度，指的是元素内容的宽度和高度，
而在 Quirks  模式下，IE 的宽度和高度还包含了 padding 和 border。
（2）在 Standards 模式下，给<span>等行内元素设置 wdith 和 height 都不会生效，而在 quirks 模式下，则会生效。
（3）设置百分比的高度：在 standards 模式下，一个元素的高度是由其包含的内容来决定的，如果父元素没有设置百分比的高度，子元素设置一个百分比的高度是无效的

对 WEB 标准以及 W3C 的理解与认识
标签闭合、标签小写、不要乱嵌套、提供seo、使用外链的css和js 表现、结构、行为分离

h5新特性
1、drag and drop拖放api  2、语义化更好的内容标签（header,nav,footer,aside,article,section） 3、音频、视频 API(audio,video) 4、Canvas 5、Geolocation
6、localStorage  7、sessionStorage  8、表单控件date time  9、新的技术 webworker, websocket, Geolocation

h5离线缓存机制
原理：HTML5 的离线存储是基于一个新建的.appcache 文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像 cookie 一样被存储了下来。
之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。
使用方法
只要在头部加一个 manifest 属性就 ok 了

<!DOCTYPE>声明位于位于 HTML 文档中的第一行，处于 <html> 标签之前。
作用：告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE 不存在或格式不正确会导致文档以怪异模式呈现。

webpack 静态模块打包器，当webpack处理应用程序，递归构建出一个依赖关系图，将模块打包成一个bundle
loader  处理非JavaScript文件本身只理解JavaScript
entry入口
1、初始化从配置文件中读取参数 
2、确定入口文件，根据entry找到入口文件
3、开始编译用上一步参数初始化一个compile对象，加载配置插件，执行对象的run方法开始编译 
4、编译模块 调用所有loader对模块翻译，找出模块的依赖
5、完成模块编译，得到每个模块翻译的内容和它们之间的依赖关系
6、输出资源，根据入口和模块之间的依赖关系组装成多个模块的chunk
7、根据输出路径输出 

webpack.config.js

vuecli通过webpack-chain维护的vue.config.js
module.exports = {
    chainWebpack: config => {
        config.module
            .rule('vue')
            .use('vue-loader')
                .loader('vue-loader')
                .tap(option => {
                    return options
                })
    }
}

解决跨域 jsonp  cros   proxy   websockets  nginx配置反向代理接口跨域
vuecli3   devserver中配置proxy 将api请求代理到api服务器上
cros中node后端配置Access-Control-Allow-Origin:"*"


Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型。
 //CommonJS中,模块使用module.exports和exports,不适合浏览器环境。nodo中用的是CommonJS规范，使用require引入模块，使用module.exports导出接口。
        // MD和CMD最大的区别是对依赖模块的执行时机处理不同，而不是加载的时机或者方式不同，二者皆为异步加载模块。
        // AMD依赖前置，js可以方便知道依赖模块是谁，立即加载；
        // 而CMD就近依赖，需要使用把模块变为字符串解析一遍才知道依赖了那些模块，这也是很多人诟病CMD的一点，牺牲性能来带来开发的便利性，实际上解析模块用的时间短到可以忽略。
        //ES6标准发布后，module成为标准，标准使用是以export指令导出接口，以import引入模块

v-if 和 v-show的区别
v-if 在条件切换时会对标签进行适当的创建和销毁
v-show 条件是否成立都会渲染标签，它仅仅是简单的css切换  频繁切换用v-show

vue“渐进式”：是指先使用vue核心库，在vue核心库的基础上，根据自己需要再去逐渐增加功能。
Vue的核心的功能，是一个视图模板引擎，但这不是说Vue就不能成为一个框架。
在声明式渲染（视图模板引擎）的基础上，我们可以通过添加组件系统、客户端路由、大规模状态管理来构建一个完整的框架。
更重要的是，这些功能相互独立，你可以在核心功能的基础上任意选用其他的部件，不一定要全部整合在一起。
所说的“渐进式”，其实就是Vue的使用方式，同时也体现了Vue的设计的理念。

每个 Vue 实例在被创建时都要经过一系列的初始化过程——
例如，需要设置数据监听、编译模板、将实例挂载到 DOM 并在数据变化时更新 DOM 等。
同时在这个过程中也会运行一些叫做生命周期钩子的函数，这给了用户在不同阶段添加自己的代码的机会。
vue实例创建到销毁的过程
beforeCreate created beforeMount mounted beforeUpdate updated beforeDestroy  destroyed   activated() deactivated() 主要是配合keep-alive

import 和 require的区别
遵循规范
require 是 AMD规范引入方式
import是es6的一个语法标准，如果要兼容浏览器的话必须转化成es5的语法
调用时间
require是运行时调用，所以require理论上可以运用在代码的任何地方（虽然这么说但是还是一般放开头）
import是编译时调用，所以必须放在文件开头

本质
require是赋值过程，其实require的结果就是对象、数字、字符串、函数等，再把require的结果赋值给某个变量
import是解构过程，但是目前所有的引擎都还没有实现import，我们在node中使用babel支持ES6，也仅仅是将ES6转码为ES5再执行，import语法会被转码为require

如何动态绑定路由信息，拦截器怎么用？

nextTick的作用

闭包的使用场景（1）通过循环给页面上的多个dom绑定事件 （2）封装变量私有变量 （3）延续变量的寿命
访问父函数的参数并且能立即执行或者被直接return出来的函数为闭包
闭包就是能够读取其他函数内部变量的函数。

this永远指向的是最后调用它的对象
箭头函数里面的this是在定义它时绑定的，指向它的父级作用域，而不是调用它对象，这个this的指向是不能通过call和apply改变的。

1、cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递，而sessionStorage和localStorage不会自动把数据发送给服务器，仅在本地保存。cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下 
2、存储大小限制也不同，cookie数据不能超过4K，同时因为每次http请求都会携带cookie、所以cookie只适合保存很小的数据，如会话标识。sessionStorage和localStorage虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大 
3、数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭之前有效；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie：只在设置的cookie过期时间之前有效，即使窗口关闭或浏览器关闭 
4、作用域不同，sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；localstorage在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的 
5、web Storage支持事件通知机制，可以将数据更新的通知发送给监听者 
6、web Storage的api接口使用更方便
