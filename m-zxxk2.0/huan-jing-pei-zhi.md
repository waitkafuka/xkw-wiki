# 重要参数
## 测试环境
测试环境`nginx`：`10.1.5.69`   
测试服务器：`10.1.1.40`，端口`3000`  
## 生产环境   
生产环境`nginx`: `112.124.52.241`  
生产服务器1：`120.55.101.59`，对应内网ip： `10.117.209.210`，端口`3000 `  
生产服务器2：`121.41.77.58`，对应内网ip：`10.168.229.119`，端口`3000`  
# Node.js
不管是开发、测试还是生产环境，都需要首先安装`Node.js`。`Node.js`是后端渲染和npm模块管理的重要前提。`Node.js`的安装和npm的使用在上次`gulp的使用方法`培训中已经讲过，可以登录oa后下载查看这个课件：<http://oa.zxxk.com/kindeditor/attached/2018/12/file/20181206170422_3934.pptx>

# 开发环境
开发环境需要完整模拟测试和生产环境（除了启动方式），需要在本地安装`nginx`，配置`host`和`dns`。
## nginx配置
`nginx`的`server`节点的配置如下：
```
server {
    listen       80;
    server_name m2.zxxk.com;
    location /_nuxt/ {
        proxy_pass http://127.0.0.1:3000/_nuxt/;
    }

    location /__webpack_hmr/ {
        proxy_pass http://127.0.0.1:3000/__webpack_hmr/;
    }

    location ~* ^/soft/(\d+).html {
        set $softid $1;
        if ($query_string ~* "^t=v$" ){
            proxy_pass http://10.1.1.40:9002/soft/$softid.html;
        }
        proxy_pass http://127.0.0.1:3000/soft/$softid;
    }

    location /api/ {
        proxy_pass http://10.1.1.40:18121/api/;
    }
}
```
## host配置
需要在本地`host`文件添加映射：  
`127.0.0.1 m2.zxxk.com`
## dns配置
需要设置本机dns为`10.1.1.3`  

## 代码环境
首先将代码拉取到本地：  
`git clone http://git.corp.zxxk.com/m/m-zxxk2.0.git`  
然后**cd进入项目web目录**下，安装项目依赖：  
`npm i`  
启动开发服务器，实时监控代码并实现热重载：  
`npm run dev`   
在浏览器中输入<http://m2.zxxk.com:3000/soft/65656.html>即可访问  

# 测试环境配置
测试环境需要安装`pm2`。
## pm2安装和配置
第一步，全局安装`pm2`：  
`npm i -g pm2`  
第二步，全局安装`pm2`日志组件：  
`pm2 install pm2-logrotate`  
第三步，设置日志参数，这里设置了日志的最大体积达到100M会自动分割文件，数量超过365个时会自动删除之前的旧文件：  
`pm2 set pm2-logrotate:max_size 100M`  
`pm2 set pm2-logrotate:retain 365`  

## nginx配置
测试环境和研一共用一个`nginx`，服务器ip为`10.1.5.69`，所用配置文件和本地的配置基本相同。

## host配置
需要将测试服务器解析指向测试的`nginx`服务器：
`10.1.5.69 m2.zxxk.com`

## 代码环境
测试环境服务器ip为`10.1.1.40`。  
首先进入项目根目录：  
`D:\gitlab\m-zxxk2.0\web`  
更新代码：  
`git pull`  
如果有新增`npm`包需要执行安装：  
`npm i`  
进行构建：  
`npm run build`
第一次启动服务：
`pm2 start startup.js`
之后每次更新无需重启，只需在`git pull`和`npm run build`之后，执行：  
`pm2 reload all`  
即可。  

# 访问测试环境
如果要在本地访问测试环境，只需修改dns配置为`10.1.1.3`即可。  
访问地址为<http://m2.zxxk.com>。  
**注意：如果更改了`host`文件，需要删除`host`文件中`m2.zxxk.com`的配置。**

# 生产环境
生产环境采用分布式部署，分别在`120.55.101.59`和`121.41.77.58`上各自启动一个节点，通过`nginx`配置负载均衡。  
生产环境配置和测试服务器的完全一样。唯一不同的是`nginx`配置。  
## nginx配置
`nginx`部署在`112.124.52.241`上，所用配置为：
```
location ~* ^/soft/(\d+).html {
    set $softid $1;
    if ($http_user_agent ~* "360spider|qihoobot|Baiduspider|Googlebot|Googlebot-Mobile|Googlebot-Image|Mediapartners-Google|Adsbot-Google|Feedfetcher-Google|Yahoo! Slurp|Yahoo! Slurp China|YoudaoBot|Sosospider|Sogou spider|Sogou web spider|MSNBot|ia_archiver|Tomato Bot") {
        proxy_pass http://Msoft-pachong;
    }
    if ($query_string ~* "^t=v$" ){
        proxy_pass http://newM/soft/$softid.html;
    }
    proxy_pass http://newM2/soft/$softid;
}
location /_nuxt/ {
    proxy_pass http://newM2;
}

upstream newM2 {
    server 10.117.209.210:3000 max_fails=5 fail_timeout=30s;
    server 10.168.229.119:3000 max_fails=5 fail_timeout=30s;
}
```