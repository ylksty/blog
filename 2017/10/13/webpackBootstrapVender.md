## [webpack](../webpack.md)/webpack2生成代码分析2(webpackBootstrap+vender)/[prev](../12/webpackBootstrap.md)/[next](./webpackBootstrapVenderManifest.md)
### [blog](../../../README.md)/[2017](../../README.md)/[10](../README.md)/12
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
})
~~~
### 说明
* 入口文件和包含文件还是上节那几个
* 第一步：vender.js首先执行，完成 webpackJsonp 函数的初始化
* 第二步：index.js然后执行 webpackJsonp
* 关于__webpack_require__.e 参考 [webpack产出代码模块化浅析][1]

### 编译完文件
* vender.js
~~~js
 (function(modules) { // webpackBootstrap
 	// install a JSONP callback for chunk loading
 	var parentJsonpFunction = window["webpackJsonp"];
 	window["webpackJsonp"] = function webpackJsonpCallback(chunkIds, moreModules, executeModules) {
 		// add "moreModules" to the modules object,
 		// then flag all "chunkIds" as loaded and fire callback
 		var moduleId, chunkId, i = 0, resolves = [], result;
 		for(;i < chunkIds.length; i++) {
 			chunkId = chunkIds[i];
 			if(installedChunks[chunkId]) {
 				resolves.push(installedChunks[chunkId][0]);
 			}
 			installedChunks[chunkId] = 0;
 		}
 		for(moduleId in moreModules) {
 			if(Object.prototype.hasOwnProperty.call(moreModules, moduleId)) {
 				modules[moduleId] = moreModules[moduleId]; // 获得模块 modules
 			}
 		}
 		if(parentJsonpFunction) parentJsonpFunction(chunkIds, moreModules, executeModules); // 处理之前的chunk
 		while(resolves.length) {
 			resolves.shift()(); // 取出删除第一个并执行
 		}
 		if(executeModules) { // 入口模块，可以有多个
 			for(i=0; i < executeModules.length; i++) {
 				result = __webpack_require__(__webpack_require__.s = executeModules[i]);
 			}
 		}
 		return result;
 	};

 	// The module cache
 	var installedModules = {};

 	// objects to store loaded and loading chunks
 	var installedChunks = {
 		1: 0
 	};

 	// The require function
 	function __webpack_require__(moduleId) {

 		// Check if module is in cache
 		if(installedModules[moduleId]) {
 			return installedModules[moduleId].exports;
 		}
 		// Create a new module (and put it into the cache)
 		var module = installedModules[moduleId] = {
 			i: moduleId,
 			l: false,
 			exports: {}
 		};

 		// Execute the module function
 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);

 		// Flag the module as loaded
 		module.l = true;

 		// Return the exports of the module
 		return module.exports;
 	}

 	// This file contains only the entry chunk.
 	// The chunk loading function for additional chunks
 	__webpack_require__.e = function requireEnsure(chunkId) {
 		var installedChunkData = installedChunks[chunkId];
 		if(installedChunkData === 0) {
 			return new Promise(function(resolve) { resolve(); });
 		}

 		// a Promise means "currently loading".
 		if(installedChunkData) {
 			return installedChunkData[2];
 		}

 		// setup Promise in chunk cache
 		var promise = new Promise(function(resolve, reject) {
 			installedChunkData = installedChunks[chunkId] = [resolve, reject];
 		});
 		installedChunkData[2] = promise;

 		// start chunk loading
 		var head = document.getElementsByTagName('head')[0];
 		var script = document.createElement('script');
 		script.type = 'text/javascript';
 		script.charset = 'utf-8';
 		script.async = true;
 		script.timeout = 120000;

 		if (__webpack_require__.nc) {
 			script.setAttribute("nonce", __webpack_require__.nc);
 		}
 		script.src = __webpack_require__.p + "js/" + chunkId + ".js";
 		var timeout = setTimeout(onScriptComplete, 120000);
 		script.onerror = script.onload = onScriptComplete;
 		function onScriptComplete() {
 			// avoid mem leaks in IE.
 			script.onerror = script.onload = null;
 			clearTimeout(timeout);
 			var chunk = installedChunks[chunkId];
 			if(chunk !== 0) {
 				if(chunk) {
 					chunk[1](new Error('Loading chunk ' + chunkId + ' failed.'));
 				}
 				installedChunks[chunkId] = undefined;
 			}
 		};
 		head.appendChild(script);

 		return promise;
 	};

 	// expose the modules object (__webpack_modules__)
 	__webpack_require__.m = modules;

 	// expose the module cache
 	__webpack_require__.c = installedModules;

 	// define getter function for harmony exports
 	__webpack_require__.d = function(exports, name, getter) {
 		if(!__webpack_require__.o(exports, name)) {
 			Object.defineProperty(exports, name, {
 				configurable: false,
 				enumerable: true,
 				get: getter
 			});
 		}
 	};

 	// getDefaultExport function for compatibility with non-harmony modules
 	__webpack_require__.n = function(module) {
 		var getter = module && module.__esModule ?
 			function getDefault() { return module['default']; } :
 			function getModuleExports() { return module; };
 		__webpack_require__.d(getter, 'a', getter);
 		return getter;
 	};

 	// Object.prototype.hasOwnProperty.call
 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };

 	// __webpack_public_path__
 	__webpack_require__.p = "";

 	// on error function for async loading
 	__webpack_require__.oe = function(err) { console.error(err); throw err; };
 })
/************************************************************************/
 ([]);
~~~

* index.js
~~~js
webpackJsonp([0],[
/* 0 */
/***/ (function(module, __webpack_exports__, __webpack_require__) {

"use strict";
Object.defineProperty(__webpack_exports__, "__esModule", { value: true });
/* harmony export (binding) */ __webpack_require__.d(__webpack_exports__, "chunk1", function() { return chunk1; });
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_0__main1__ = __webpack_require__(1);
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_1__bar__ = __webpack_require__(2);
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_1__bar___default = __webpack_require__.n(__WEBPACK_IMPORTED_MODULE_1__bar__);



console.log(Object(__WEBPACK_IMPORTED_MODULE_0__main1__["c" /* f1 */])())
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["c" /* f1 */])
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["a" /* chunk2 */])
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["b" /* default */])
console.log(__WEBPACK_IMPORTED_MODULE_1__bar__)
console.log(__WEBPACK_IMPORTED_MODULE_1__bar__["ssss"])

var chunk1 = 1


/***/ }),
/* 1 */
/***/ (function(module, __webpack_exports__, __webpack_require__) {

"use strict";
/* harmony export (binding) */ __webpack_require__.d(__webpack_exports__, "a", function() { return chunk2; });
/* harmony export (immutable) */ __webpack_exports__["c"] = f1;
/* unused harmony export f2 */
var chunk2 = 2


function f1() {
  return 'f1';
}
function f2() {
  return 'f2';
}
let chunkss = {abc: 'abc'}
/* harmony default export */ __webpack_exports__["b"] = (chunkss);

/***/ }),
/* 2 */
/***/ (function(module, exports) {

exports.ssss = 'Hello';
exports.b = 'world';
exports.c = 'what?';

/***/ })
],[0]);
~~~


[1]:http://shellphon.wang/githublog/2017/02/webpack-product.html

