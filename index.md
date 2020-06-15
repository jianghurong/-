## 前端技术栈

开发语言：Vue  
组件库:  
Pc-element  
mobile-vant  
pad-vant  
http 库：axios  
状态管理器：vuex + vuex-persist

## 代码规范

文件命名：小写，用“-”连接  
CSS 类命名：BEM 规范  
JS 变量名：驼峰
项目目录结构:
vue.config.js 文件别名
调用 api 方式
异步调用 async await

## vue 打包 

vue.config.js

/**生产环境禁止 sourceMap**/  
productionSourceMap: false  
/**设置 node_modules 中转 es5 的模块**/  
transpileDependencies: ['vuex-persist']
/**生产环境开启 gzip 压缩**/
compression-webpack-plugin

## icon 使用 svg

## 方法库

## README.md 需写上项目接口文档地址和部署的服务器，访问地址,包括正式服和测试服
