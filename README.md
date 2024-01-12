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
           
### vue2核心知识
    vue 实例（组件this.xxx）
        实例创建选项
            挂载
            模版
            数据

            选项 / 数据
                data
                props
                propsData
                computed
                methods
                watch
            选项 / DOM
                el
                template
                render
                renderError
            选项 / 生命周期钩子
                beforeCreate
                created
                beforeMount
                mounted
                beforeUpdate
                updated
                activated
                deactivated
                beforeDestroy
                destroyed
                errorCaptured
            选项 / 资源
                directives
                filters
                components
            选项 / 组合
                parent
                mixins
                extends
                provide / inject
            选项 / 其它
                name
                delimiters
                functional
                model
                inheritAttrs
                comments
    
        属性
            $props
            $data
                app.text = 1
                app.$data.text = 1
            $el
            $options
                app.$options.render = () => {}
            $root === app 根组件  
            $children 子组件
            $slots、$scopedSlotes
            $refs
            $isServer 

            vm.$data
            vm.$props
            vm.$el
            vm.$options
            vm.$parent
            vm.$root
            vm.$children
            vm.$slots
            vm.$scopedSlots
            vm.$refs
            vm.$isServer
            vm.$attrs
            vm.$listeners

        方法
            挂载$mount
            $watch
            $on、$once、$emit
            $forceUpdate
            $set
            $nextTick
            实例方法 / 数据
                vm.$watch
                vm.$set
                vm.$delete
            实例方法 / 事件
                vm.$on
                vm.$once
                vm.$off
                vm.$emit
            实例方法 / 生命周期
                vm.$mount
                vm.$forceUpdate
                vm.$nextTick
                vm.$destroy

    vue组件生命周期、调用顺序
        $mount
            beforeCreate（ssr）
            created（ssr）
            beforeMount
            Mounted（dom）    
        app.text + 1
            beforeUpdate
            updated
        $destroy
            beforeDestroy
            destroyed            
            
            