## 利用Apache bench（ab）进行接口压力测试

```shell
ab -n 1 -c 1 -p post.json -T application/json http://xxx.xxx.xxx.xxx/xxxx
```

-n 总请求数(缺省为1) / -c 并发请求数(缺省为1) / -p 指定post方法数据文件 / -T 指定contentType