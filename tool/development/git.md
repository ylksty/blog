## root/[tool](../README.md)/development/git
### 文档
* [看这个就够了](https://github.com/geeeeeeeeek/git-recipes/wiki)

###Git配置 `用户的git配置文件~/.gitconfig`
~~~
git config --global credential.helper store # 保存用户名密码
git config --global user.name "yanglk"
git config --global user.email "ylksty@163.com"
git config --global color.ui true
git config --global alias.co checkout  # 别名
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global core.editor "vim"  # 设置Editor使用vim
git config --global core.quotepath false # 设置显示中文文件名
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h %p%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global push.default matching
~~~
~~~
git config --global credential.helper store
git config --global user.name "yanglk"
git config --global user.email "ylksty@163.com"
git config --global color.ui true
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global core.editor "vim"
git config --global core.quotepath false
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h %p%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global push.default matching
~~~

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

### 优雅地删除远程一个版本
* git reset HEAD~1
* git push origin :abc

### 优雅地删除本地一个版本
* git reset --hard xxx

### ssh-keygen -t rsa -C "xxx@163.com"

### 第一次上传
* git push -u origin master
* git push -u -f origin master

### 把版本库已有的一部分内容去掉
* git rm -r --cached static

### fork后如何同步源的新更新内容
* git remote add upstream https://github.com/museui/muse-ui.git
* git fetch upstream
* git checkout master
* git merge upstream/master
* git push origin master
