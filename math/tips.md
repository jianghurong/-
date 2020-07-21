1.安装mathtype-generic模块(必须指定版本，否则可能出现异常)
```js
npm i @wiris/mathtype-generic@7.21.0
or
yarn add @wiris/mathtype-generic@7.21.0
```
2.公式编辑器面板“取消”按钮显示异常  
解决：在node_moudules中
```
@wiris/mathtype-generic/wirisplugin-generic.js
```
搜索“�?�消”然后替换成“取消”
