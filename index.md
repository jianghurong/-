## 前端技术栈

开发语言：Vue  
组件库:  
Pc-element  
mobile-vant  
pad-vant  
http库：axios  
状态管理器：vuex + vuex-persist


## 代码规范
文件命名：小写，用“-”连接    
CSS类命名：BEM规范  
JS变量名：驼峰

## vue打包
vue.config.js

/**生产环境禁止sourceMap**/  
productionSourceMap: false  
/**设置node_modules中转es5的模块**/  
transpileDependencies: ['vuex-persist']

## icon使用svg
