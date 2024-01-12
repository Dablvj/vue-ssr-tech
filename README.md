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
    