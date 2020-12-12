




```
＃mycontentをマウントしてnginx 起動 
$ docker run --rm --name fluentd-example-nginx \
    -v $(pwd)/mycontent:/usr/share/nginx/html:ro \
    -v $(pwd)/nginx/conf.d:/etc/nginx/conf.d:ro \
    --mount type=bind,source=$PWD/mycontent,target=/usr/share/nginx/html \
    --mount type=bind,source=$PWD/nginx/conf.d,target=/etc/nginx/conf.d \
    --mount type=bind,source=$PWD/nginx/nginx.conf,target=/etc/nginx/nginx.conf \
    -p 8080:80 \
    -d nginx
```


```
＃/var/log/nginxをマウントしてnginx 起動 
docker run --rm --name fluentd-example-nginx \
    --mount type=bind,source=$PWD/mycontent,target=/usr/share/nginx/html \
    --mount type=bind,source=$PWD/nginx/conf.d,target=/etc/nginx/conf.d \
    --mount type=bind,source=$PWD/nginx/nginx.conf,target=/etc/nginx/nginx.conf \
    --mount type=bind,source=$PWD/nginx/mylog,target=/var/log/nginx \
    -p 8080:80 \
    -d nginx
```

docker run --rm --name fluentdtest \
    --mount type=bind,source=$PWD/config,target=/fluentd/etc \
    --mount type=bind,source=/Users/takuya/nginx-fluentd-example/web/nginx/mylog,target=/var/log/nginx \
    -p 24224:24224 \
    myfluentd:latest








