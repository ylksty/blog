## root/[operationAndMaintenance](../README.md)/linux/sftp
### [如何在Ubuntu下安装和配置FTP服务器](https://yq.aliyun.com/articles/192972)
### <http://wiki.ubuntu.org.cn/Vsftpd>

## pit
### 把用户从一个分组去掉 (把用户的分组信息清空)
* sudo usermod -G  '' yanglk

### 把权限限制在 home/用户 使其他目录文件不能上传和下载
~~~
chroot_local_user=YES
chroot_list_enable=NO
chroot_list_file=/etc/vsftpd.chroot_list
~~~