### [webpack](../webpack.md)/webpack2生成代码分析3(webpackBootstrap+vender+manifest)/[prev](./webpackBootstrapVender.md)
### [blog](../../../README.md)/[2017](../../README.md)/[10](../README.md)/13
### 配置文件添加
~~~js
// split vendor js into its own file
new webpack.optimize.CommonsChunkPlugin({
  name: 'vendor',
  minChunks: function (module, count) {
    // any required modules inside node_modules are extracted to vendor
    return (
      module.resource &&
      /\.js$/.test(module.resource) &&
      module.resource.indexOf(
        config.nodemPath
      ) === 0
    )
  }
}),
new webpack.optimize.CommonsChunkPlugin({
  name: "manifest",
  chunks: ['vendor']
}),
~~~
### 说明
* 入口文件和包含文件还是上节那几个
* main.js引入vue模块

### main.js
~~~js
import chunks, { f1, chunk2 } from './main1'
import * as Bar from './bar'
import Vue from 'vue'
new Vue({
  created () {
    console.log('vue')
  }
})

console.log(f1())
console.log(f1)
console.log(chunk2)
console.log(chunks)
console.log(Bar)
console.log(Bar.ssss)

var chunk1 = 1
export {chunk1}
~~~

### 编译完文件
* manifest.js // webpackJsonp函数初始化
~~~js
(function(modules) { // webpackBootstrap
    ...
 })([]);
~~~

* vender.js // node_modules模块
~~~js
webpackJsonp([0],[...])
~~~

* index.js // main.js及引入的模块
~~~js
webpackJsonp([0],[...],[0])
~~~
