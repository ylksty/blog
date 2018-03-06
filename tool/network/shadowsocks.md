## root/[tool](../README.md)/network/shadowsocks

### 各种坑
* 一直用朋友的ss账号，最近不能用了，忍不了，自己整一个
* 两天时间从阿里云香港服务器，到aws，弄了各遍
* 最后发现香港服务器把，sslocal改成ssserver就好了

### 拾遗
* 各种命令
~~~
sudo ssserver -c /etc/ss/config.json -d start
sudo ssserver -c /etc/ss/config.json -d stop
sudo ssserver -c /etc/ss/config.json -d restart
~~~
* 日志目录在哪？
~~~
tail -f /var/log/ss.log
~~~

* 设置开机启动
~~~
在/etc/rc.local中加入
#start the shadowsocks server
sudo ssserver -c /etc/ss/config.json -d start
~~~

* 配置
  * sudo vim /etc/shadowsocks/config.json
~~~
{
    "server":"0.0.0.0",
    "server_port":443,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"xxxxx",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open":false,
    "workers":5
}
~~~

* 端口查看？
~~~
netstat -nt
~~~

* sh脚本
~~~
#！/bin/bash
#shadow.sh
ssserver -c /etc/shadowsocks/config.json -d start
~~~

* 查看本机网路
  * curl cip.cc
  
### 相关参考
  * [aws](http://blog.csdn.net/f59130/article/details/74014415)
    * export LC_ALL=C
  
  * [Shadowsocks原理和搭建](http://blog.021xt.cc/archives/98)
  
  * [使用ssh正向连接、反向连接、做socks代理的方法](http://www.jianshu.com/p/a49848a063e7)
  
  * [科学上网之 Shadowsocks 安装及优化加速](https://yq.aliyun.com/articles/137280?commentId=11711)
    * aliyun
  
  * [aws搭建shadowsocks服务器](http://blog.csdn.net/hacker_700/article/details/71474120)
  
  * [linux 下添加用户并赋予root权限](http://blog.csdn.net/du_minchao/article/details/52170415)
  
  * [github的Troubleshooting](https://github.com/shadowsocks/shadowsocks/wiki/Troubleshooting)
  
  * [使用shadowsocks轻松搭建翻墙环境教程](https://blog.phpgao.com/shadowsocks_on_linux.html/comment-page-3#comments)
    * 老高
  
  * [ShadowSocks 自定义规则](http://honglu.me/2015/06/26/ShadowSocks%E8%87%AA%E5%AE%9A%E4%B9%89%E8%A7%84%E5%88%99/)