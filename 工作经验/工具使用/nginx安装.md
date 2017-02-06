## Nginx安装

- nginx安装与常用命令
- 配置文件路径
- nginx执行常见错误


==nginx安装与常用命令==

在命令行更新软件然后安装nginx：
```
sudo apt-get update
sudo apt-get install nginx
```

等待安装完成后，检查安装是否成功
```
ps aux |grep nginx 或者 netstat -tnl |grep 80
```

启动nginx可以使用下面命令
```
sudo nginx -c /etc/nginx/nginx.conf
sudo nginx
```

重启nginx可以使用下面命令
```
sudo nginx -s reload
```

停止nginx可以使用下面命令
```
sudo nginx -s quit 或者 sudo nginx -s stop
```
==配置文件路径==
进入/etc/nginx/conf.d目录下创建 wuxc.oicp.net.conf文件，设定虚拟主机配置在文件中增加下面内容，保存后重启nginx生效了。

```
	#设定虚拟主机配置
	server {
		#侦听80端口
		listen    80;
		#定义使用 www.nginx.cn访问
		server_name wuxc.oicp.net；
		#默认请求
		location / {
			proxy_pass http://127.0.0.1:8080;
			proxy_redirect off;
			proxy_set_header X-Real-IP $remote_addr;
			#后端的Web服务器可以通过X-Forwarded-For获取用户真实IP
            #以下是一些反向代理的配置，可选。
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			proxy_set_header Host $host;
			client_max_body_size 10m; #允许客户端请求的最大单文件字节数
			client_body_buffer_size 128k; #缓冲区代理缓冲用户端请求的最大字节数，
			proxy_connect_timeout 90; #nginx跟后端服务器连接超时时间(代理连接超时)
			proxy_send_timeout 90; #后端服务器数据回传时间(代理发送超时)
			proxy_read_timeout 90; #连接成功后，后端服务器响应时间(代理接收超时)
			proxy_buffer_size 4k; #设置代理服务器（nginx）保存用户头信息的缓冲区大小
			proxy_buffers 4 32k; #proxy_buffers缓冲区，网页平均在32k以下的设置
			proxy_busy_buffers_size 64k; #高负荷下缓冲大小（proxy_buffers*2）
			proxy_temp_file_write_size 64k;#设定缓存文件夹大小，大于这个值，将从upstream服务器传
		}
	}
```


==nginx执行常见错误==

一些常见的错误，首次安装完后重启nginx会出现下面错误，由于启动没有指定配置
```
[error] 19465#0: open() "/run/nginx.pid" failed (2: No such file or directory)
```
