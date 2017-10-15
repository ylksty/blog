#### Component template should contain exactly one root element. If you are using v-if on multiple elements, use v-else-if to chain them instead.
* 错误示范
~~~html
<template>
  <img src="../assets/favicon.jpeg">
</template>
~~~
> webpack处理 `img` 标签的时候会把它当做一个组件，必须有个根节点，所以
* 正确处理
~~~html
<template>
<div>
  <img src="../assets/favicon.jpeg">
</div>
</template>
~~~