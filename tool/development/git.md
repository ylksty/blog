## root/[tool](../README.md)/development/git
### 文档
* [看这个就够了](https://github.com/geeeeeeeeek/git-recipes/wiki)

### Github上fork项目后保持与源项目更新
~~~
git remote add laradock https://github.com/laradock/laradock.git
git remote -v
git co master
git pull laradock master // 更新最新master到本地
git fetch ups --tags // 更新最新版本到本地
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
rm -rf nodewww
git submodule add --force ... nodewww
~~~

### 标签删除
~~~
git tag -d <tagname>
git push origin :refs/tags/<tagname>
~~~

### 删除远端分支
~~~
git push origin :branch-name
~~~

### 默认对文件名大小写不敏感 (不区分文件名大小写)
* git config core.ignorecase false


### 添加子模块
* git submodule add https://git.oschina.net/ylkget/yii2_vendor.git vendor