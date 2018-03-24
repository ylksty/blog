## root/[operationAndMaintenance](../README.md)/linux/pit
### 端口被占用怎么办？
* lsof -i tcp:7001

### is not in the sudoers file
* chmod u+w /etc/sudoers
* root ALL=(ALL) ALL
* xxx ALL=(ALL) ALL
* chmod u-w /etc/sudoers

### ll command not found
* vim ~/.bashrc
* alias ll='ls -al'

### Unable to locate package vsftpd
* sudo apt-get update