### [javascript](../../javascript.md)/vue
### [blog](../../README.md)/[2017](../README.md)/[10](README.md)/vue
### muse-ui
* <http://www.material-ui.com/#/>
* <https://material.io/icons/>
* 编辑模块不从node_modules引入
* 拾遗
> Inline JavaScript is not enabled. Is it set in your options?
  * less编译错误，把`.-;`去掉就好了
> You may need an appropriate loader to handle this file type.
  * muSrc目录没有被`babel-loader`处理
  ~~~js
  {
    test: /\.js$/,
    loader: 'babel-loader',
    include: [resolve('muSrc'), resolve('test')]
  }
  ~~~