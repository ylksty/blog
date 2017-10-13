### [webpack](../webpack.md)/webpack2生成代码分析1(webpackBootstrap)/[next](../13/webpackBootstrapVender.md)
### [blog](../../../README.md)/[2017](../../README.md)/[10](../README.md)/12
### 说明
* 执行编译

### main.js
~~~js
import chunks, { f1, chunk2 } from './main1'
import * as Bar from './bar'

console.log(f1())
console.log(f1)
console.log(chunk2)
console.log(chunks)
console.log(Bar)
console.log(Bar.ssss)

var chunk1 = 1
export {chunk1}
~~~

### main1.js
~~~js
var chunk2 = 2
export {chunk2}

export function f1() {
  return 'f1';
}
export function f2() {
  return 'f2';
}
let chunkss = {abc: 'abc'}
export default chunkss
~~~

### bar.js
~~~
exports.ssss = 'Hello';
exports.b = 'world';
exports.c = 'what?';
~~~

### 编译结果
~~~js
 (function(modules) { // webpackBootstrap
 	// The module cache (已处理模块缓存)
 	var installedModules = {};

 	// The require function
 	function __webpack_require__(moduleId) {

 		// Check if module is in cache (检查是否已缓存)
 		if(installedModules[moduleId]) {
 			return installedModules[moduleId].exports;
 		}
 		// Create a new module (and put it into the cache) (新建模块，保存import模块处理结果，并保存缓存)
 		var module = installedModules[moduleId] = {
 			i: moduleId,
 			l: false,
 			exports: {}
 		};

 		// Execute the module function (主要是处理 module.exports)
 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);

 		// Flag the module as loaded (标记处理成功)
 		module.l = true;

 		// Return the exports of the module
 		// 返回处理结果
 		return module.exports;
 	}


 	// expose the modules object (__webpack_modules__)
 	__webpack_require__.m = modules;

 	// expose the module cache
 	__webpack_require__.c = installedModules;

 	// define getter function for harmony exports (定义为和谐模块输出定义方法)
 	__webpack_require__.d = function(exports, name, getter) {
 		if(!__webpack_require__.o(exports, name)) {
 			Object.defineProperty(exports, name, {
 				configurable: false,
 				enumerable: true,
 				get: getter
 			});
 		}
 	};

 	// getDefaultExport function for compatibility with non-harmony modules (处理不和谐模块)
 	__webpack_require__.n = function(module) {
 		var getter = module && module.__esModule ?
 			function getDefault() { return module['default']; } :
 			function getModuleExports() { return module; };
 		__webpack_require__.d(getter, 'a', getter);
 		return getter;
 	};

 	// Object.prototype.hasOwnProperty.call (检查对象是否有指定的属性)
 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };

 	// __webpack_public_path__
 	__webpack_require__.p = "";

 	// Load entry module and return exports (载入入口模块并返回输出)
 	return __webpack_require__(__webpack_require__.s = 0);
 })
/************************************************************************/
 ([
/* 0 */
/***/ (function(module, __webpack_exports__, __webpack_require__) { // 入口模块 main

"use strict";
Object.defineProperty(__webpack_exports__, "__esModule", { value: true }); // 定义为和谐模块
/* harmony export (binding) */ __webpack_require__.d(__webpack_exports__, "chunk1", function() { return chunk1; }); // 把输出附上属性chunk1
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_0__main1__ = __webpack_require__(1); // 获得main1模块
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_1__bar__ = __webpack_require__(2);
/* harmony import */ var __WEBPACK_IMPORTED_MODULE_1__bar___default = __webpack_require__.n(__WEBPACK_IMPORTED_MODULE_1__bar__);
    console.log(__WEBPACK_IMPORTED_MODULE_1__bar___default() === __WEBPACK_IMPORTED_MODULE_1__bar__) // true


console.log(Object(__WEBPACK_IMPORTED_MODULE_0__main1__["c" /* f1 */])()) // 获得main1模块的f1方法，并执行
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["c" /* f1 */]) // __webpack_exports__["c"] = f1
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["a" /* chunk2 */]) // 从__webpack_require__.d
console.log(__WEBPACK_IMPORTED_MODULE_0__main1__["b" /* default */]) // 从__webpack_exports__["b"]
console.log(__WEBPACK_IMPORTED_MODULE_1__bar__)
console.log(__WEBPACK_IMPORTED_MODULE_1__bar__["ssss"])

var chunk1 = 1


/***/ }),
/* 1 */
/***/ (function(module, __webpack_exports__, __webpack_require__) { // main1模块

"use strict";
/* harmony export (binding) */ __webpack_require__.d(__webpack_exports__, "a", function() { return chunk2; }); // 暴露属性到输出
/* harmony export (immutable) */ __webpack_exports__["c"] = f1; // 暴露f1方法到输出
/* unused harmony export f2 */ // f2方法没有被调用，所以，没有暴露
var chunk2 = 2


function f1() {
  return 'f1';
}
function f2() {
  return 'f2';
}
let chunkss = {abc: 'abc'}
/* harmony default export */ __webpack_exports__["b"] = (chunkss); // 暴露 default， 直接暴露

/***/ }),
/* 2 */
/***/ (function(module, exports) {

exports.ssss = 'Hello';
exports.b = 'world';
exports.c = 'what?';

/***/ })
 ]);
~~~