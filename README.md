# Nginx

## 文件目录

`cd /etc/nginx`

## 更新

`git pull`

## 操作

- 查看状态
  `systemctl status nginx`
- 开启
  `systemctl start nginx`
- 停止
  `systemctl stop nginx`
- 重启
  `systemctl restart nginx`

## 反向代理配置

```js
	upstream home {
	    server 127.0.0.1:3000;
	    #server 127.0.0.1:8888;
	    keepalive 64;
	}

	server {
	    listen 80;
	    server_name api.hankc.cn;
	    location / {
	        proxy_set_header X-Real-IP $remote_addr;
	        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	        proxy_set_header Host  $http_host;
	        proxy_set_header X-Nginx-Proxy true;
	        proxy_set_header Connection "";
	        proxy_pass      http://home;
	    }

	}
```

## 压缩文件

- 压缩
  `tar -cvf examples.tar files|dir`
- 解压
  `tar -xvf examples.tar （解压至当前目录下)`
  `tar -xvf examples.tar -C /path (/path 解压至其它路径)`

## scp 传输文件

- `scp [可选参数] file_source file_target`
- `scp [本地文件] hankc@123.123.1.1:/home/root/others/music`

## 代理映射

- 主页 www.hankc.cn 3000
- 京东 jd.hankc.cn 3001
- 美团 mt.hankc.cn 3002
- 新闻 news.hankc.cn 3003
- CMS cms.hankc.cn 3004
- API api.hankc.cn 3005
- 简历 rs.hankc.cn 3006
- 博客 blog.hankc.cn 3007

- 游戏
- xxoo xxoo.hankc.cn 4001
