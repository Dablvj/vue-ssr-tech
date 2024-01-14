## 技术点

全面知识点讲解、深入讲解服务端渲染
80%以上时间都在详细讲解技术点
vue 项目开发
vue+webpack 工作流搭建
vue+vue-router+vuex 项目架构
vue 服务端渲染深度集成

#### 1

![](/books/2024-01-11-14.49.18.png)


### webpack4 升级

    2018.2.14 webpack4发布

    版本变化
        插件、loader的api都发生变化
    配置变化
    插件、loader变化

    webpack4升级指北
### Vue2+Webpack的前端工程工作流搭建
    vue-cli创建vue2项目
        项目目录升级正式项目目录结构
            webpack-merge 合并webpack配置
    vue-loader配置（vue-loader.config.js）
        配合vue-style-loader css热重载
        stylus-loader Stylus 
        cssModules
            样式类名格式
            $style.mainHeader:js引用类名的命名规则：小驼峰命名（css中类名是中划线式命名，js变量不能.式读取，必须数组）
                驼峰命名、中划线式命名、下划线式命名
            css-loader 也可以cssModule模式，针对import css  
        根据环境变量生成vue组件热重载
        自定义模块loader：html-loader bable-loader style-loader doc-loader
        preLoader
        postLoader
    rimraf dist
    postcss浏览器前缀（postcss.config.js）
    eslint 
        eslint-config-standard + 依赖插件 eslint官方标准规则
        eslint-plugin-html 识别vue里面js代码
        eslint --fix --ext .js\jsx\vue
        增量检查 
            babel-eslint + eslint-loader预处理
        更强制precommit钩子检查（git commit ）
            husky（.git目录生成precommit钩子） + "precommit"   
    .editorconfig+editorconfig插件 规范编辑器配置
    webpack4升级
        npm warn + TypeError undefine
        webapck3手写插件内置集成
        最后运行和build看看效果
           
### vue2核心知识（有概念）
    vue官方文档分类很清楚
        https://v2.cn.vuejs.org/v2/api/#productionTip

    vue 实例（组件this.xxx）
        实例创建选项
           
        属性
          
        方法

    vue组件生命周期、调用顺序

    vue-router、vuex集成   
### 服务端渲染构建流程
![](/books/2024-01-14-11.01.00.png)

    1. 什么是服务端渲染（SEO，首屏加载时间、服务器压力）
        服务器生成html字符串
        再发送到浏览器
    2. 渲染步骤
        1、将源码通过 webpack 打包出两个 bundle（服务端配置文件、客户端配置文件）
            1. 为什么服务端渲染最后输出 html，怎么还带 js 脚本
                1. 也就是 webpack 为什么要打包出一套服务端代码（用于渲染首次html用），一套客户端代码（用于后期交互和数据处理用）

        2、Server Bundle ：服务端通过渲染器 bundleRenderer 将 bundle 生成 html 给浏览器用；
            服务端配置文件要点：
                target：'node' 注意node端没有dom执行环境

                externals: Object.keys(require('./package.json')).dependencies  

                output.libraryTarget: 'commonjs2'：output是生成一个 commonjs 的 library  

                vue-server-renderer/server-plugin：将服务器的整个输出构建为单个 JSON 文件的插件
                    提供给require('vue-server-renderer').createBundleRenderer渲染出 html 文件

            server-entry.js要点：
                服务器的入口文件我们返回了一个 promise，因为这边 router.onReady 是异步的，所以我们返回一个 Promise确保路由组件准备就绪 

            
        2、Client Bundle：别忘了服务端只是生成前期首屏页面所需的 html ，后期的交互和数据处理还是需要能支持浏览器脚本的 Client Bundle 来完成。
            客户端配置文件要点：
                 vue-server-renderer/client-plugin：客户端构建清单 vue-ssr-client-manifest.json
                    客户端js、css路径注入到 html 一起发给浏览器

            client-entry.js要点：
                客户端代码是在路由解析完成的时候将 app 挂载到 #app 标签下

        3、vue-server-renderer npm 包，通过读取 vue-ssr-server-bundle.json 和 vue-ssr-client-manifest.json 文件 renderer 出 html

        4、服务端应用：其实上面都是准备工作，最重要的一步是将webpack构建后的资源代码给服务端用来生成 html 。我们需要用node写一个服务端应用，通过打包后的资源生成 html 并发送给浏览器    
            koa  

  
    