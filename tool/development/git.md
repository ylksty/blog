## root/[tool](../README.md)/development/git
### 文档
* [看这个就够了](https://github.com/geeeeeeeeek/git-recipes/wiki)

### [Github上fork项目后保持与源项目更新](https://segmentfault.com/a/1190000008401427)
~~~
git remote add laradock https://github.com/laradock/laradock.git
git remote -v
git co master
git pull laradock master
git push
~~~

### 优雅的删除子模块
* 逆初始化模块，其中{MOD_NAME}为模块目录，执行后可发现模块目录被清空
~~~
git submodule deinit -f nodewww
~~~
* 删除.gitmodules中记录的模块信息（--cached选项清除.git/modules中的缓存）
~~~
git rm --cached nodewww
~~~
* 提交更改到代码库，可观察到'.gitmodules'内容发生变更
~~~
git commit -am "Remove a submodule."
~~~