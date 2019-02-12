# pm2常用命令
##  启动服务
`pm2 start appName|id|all`
## 停止服务
`pm2 stop appName|id|all`
## 重载服务
**该命令常用，因为可以实现0s无缝重启，类似`nginx reload`**  
`pm2 reload appName|id|all`
## 重启服务
**该命令不常用，一般用`pm2 reload app`**  
`pm2 restart appName|id|all`  
## 删除服务
`pm2 delete appName|id|all`
## 列出所有进程列表
**常用**
`pm2 list`
## 查看所有进程的状态  
`pm2 status`
## 监控
**常用**  
`pm2 monit`
## 显示某个进程的详情
`pm2 show appName|id`
