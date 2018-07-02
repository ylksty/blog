## root/[operationAndMaintenance](../README.md)/linux/commands
### iptables
* 导出 `iptables-save > ~/iptables.bak`
* 导入 `iptables-restore < ~/iptables.bak`
* 保存 `service iptables save`

### usermod
* 同一个用户加到不同的组 usermod -G a,b user1 (重新打开链接有效)

### crontab -e