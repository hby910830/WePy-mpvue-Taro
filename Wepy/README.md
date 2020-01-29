# WePY 是什么

WePY (发音: /'wepi/) 是小程序上最早的一款类 Vue 语法的开发框架。WePY 2 是基于小程序原生组件实现组件化开发。

# 特性
- 使用 Vue Observer 实现数据绑定
- 支持 Vue watch/computed/mixin 等特性
- 基于原生组件实现组件化开发
- 支持 TypeScript

# 特点
- 开发风格：接近Vue.js，支持组件 Props 传值、自定义事件、组件分布式复用 Mixin、计算属性函数 computed、模版内容分发 slot 等。
- 组件化：组件化开发，完美解决组件隔离、组件嵌套、组件通信等问题。
- npm：支持使用第三方 npm 资源，自动处理 npm 资源之间的依赖关系，完美兼容所有平台依赖的 npm 资源包。
- Promise：通过 polyfill 让小程序完美支持 Promise，解决回调烦恼。
- ES2015：可使用 Generator Fu-nction、Class、Async Function 等特性，大大提升开发效率。
- 编译器：支持样式编译器 Less、Sass、Stylus，模版编译器 wx-ml、Pug，代码编译器 Babel、TypeScript。
- 插件：支持多种插件处理，如文件压缩、图片压缩、内容替换等，扩展简单，使用方便。
- 框架大小：压缩后有 24.3KB 空间即可拥有所有框架功能，额外增加 8.9KB 空间后即可使用 Promise 和 Async Function。

# Demo
```
<style lang="less">
    @color: #4D926F;
    .userinfo {
        color: @color;
    }
</style>
<template lang="pug">
    div(class='container')
        div(class='userinfo' @tap='tap')
            mycom(:prop='myprop' @fn='myevent')
            text {{now}}
</template>
<script>
    import wepy from '@wepy/core';

    wepy.page({
        data: {
            myprop: {}
        },
        computed: {
            now () { return new Date().getTime(); }
        },
        async onLoad() {
            await sleep(3);
            console.log('Hello World');
        },
        sleep(time) {
            return new Promise((resolve, reject) => setTimeout(resolve, time * 1000));
        },
    }
</script>
<config>
{
  usingComponents: {
    mycom: "~@/components/some-component"
  }
}
</config>
```

# 安装使用
安装（更新） wepy 命令行工具。

> npm install @wepy/cli -g

生成开发示例

> wepy init standard myproject

安装依赖

> cd myproject
>
> npm install

开发实时编译

> wepy build --watch

##### 开发者工具导入项目
使用微信开发者工具新建项目，本地开发选择项目根目录，会自动导入项目配置。