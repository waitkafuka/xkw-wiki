# 整体架构
整体采用`vue+vuex+vue-router+nuxt+webpack+es6+es8+eslint+nginx+pm2`的技术架构。  
`vue`用作数据和视图引擎，`vuex`作为全局状态管理工具，`vue-router`用来管理路由跳转和参数传递，`nuxt`作为后端渲染引擎，`webpack`打包构建，`es6`模块化，同时也用到了`es8`的部分异步编程语法，`eslint`代码格式规范检查，`nginx`反向代理和解决跨域问题，`pm2`守护`node`线程和记录`ssr`日志。
## vue
采用`vue2.5.17`作为数据和视图引擎，利用`vue-cli3`的脚手架进行搭建，具体技术细节可参考`vue-cli3`官网：[https://cli.vuejs.org/zh/guide/](https://cli.vuejs.org/zh/guide/)，在此之前需要有`vue`使用的基础，`vue`基础部分请参考`vue`官网：[https://cn.vuejs.org/v2/guide/](https://cn.vuejs.org/v2/guide/)。 
## vuex
采用`vuex`作为全局状态管理工具，具体文档请参考官网：<https://vuex.vuejs.org/zh/guide/> 
## vue-router
采用`vue-router`管理路由切换和值传递，具体文档请参考官网：<https://router.vuejs.org/zh/guide/>
## nuxt
`nuxt2.3.4`（集成了`vue2.5.17`）作为ssr框架，实现后端渲染，从而对搜索引擎友好。具体技术细节参考`nuxt`官网：[https://zh.nuxtjs.org/guide。](https://zh.nuxtjs.org/guide。)  
`nuxt`和`vue`的关系如下：  
``` 
m-zxxk@1.0.0 /Users/zks/code/gitlab/m-zxxk2.0/web  
└─┬ nuxt@2.3.4  
  └─┬ @nuxt/core@2.3.4  
    └─┬ @nuxt/vue-renderer@2.3.4  
      └── vue@2.5.17
```
## webpack
`nuxt`也集成了对`webpack`的支持并且开放了扩展接口，webpack的配置方法参考官网：<https://www.webpackjs.com/>，项目中的用法参考`nuxt.config.js`文件。
## es6
项目编码采用`es6`语法标准，`es6`语法规范可以参考这篇书籍：[http://es6.ruanyifeng.com/\#README](http://es6.ruanyifeng.com/#README)。  
项目模块化部分采用`es6`的最新标准，用`export`和`import`来定义和导入模块，利用`babel`进行转义和打包（框架中已集成）。
## es8
主要用到了`es8`的`async`和`await`异步编程语法，解决异步回调地狱问题。
## eslint
采用了`es-lint`进行代码格式的规范和格式化，编译时不规范的代码将会报错，并可结合开发工具进行按要求的格式化，也可以用命令来自动修复不规范的代码。  
代码规范遵循`vue/recommended`规则。具体规则细节查看<https://vuejs.github.io/eslint-plugin-vue/rules/>  
## nginx
`nginx`用来配置反向代理，同时解决跨域访问的问题。同时解决项目中同时也集成了`CORS`的解决方案。  
通过配置虚拟映射，`nginx`同时起到了解决新旧M站之间平滑过渡的跳转问题。
`nginx`在生产环境也起到了负载均衡的作用。  
具体`nginx`配置请查看`环境配置`章节。
## pm2
`pm2`用来解决在生产服务器上的`node`线程的守护和管理问题，例如启动、重启、监控等。  
`pm2`同时用来解决生产服务器上`SSR`部分代码的日志记录问题，以便问题发生时快速定位。
## 其他模块
其他模块请参考项目中的`package.json`文件，里面记录了项目中所有用到的模块和依赖，例如`jsonp`模块，用来兼容旧代码中支付部分的`jsonp`请求。详细用法请参考其官网：[https://www.npmjs.com/package/jsonp](https://www.npmjs.com/package/jsonp)。

# 网络图
生产环境中新旧系统之间的关系如下：  
![](../.gitbook/assets/m-zxxk2.0-network.jpg) 

