# URLPollution

> 对URL或者参数进行Payload污染 然后发送请求进行FUZZ测试 通过 dnslog ceye.io 等DNS请求记录平台辅助测试

### 用途
* 命令执行测试
* 命令注入测试
* 模板注入测试
* ......

### 参数说明
```
payload_generator(self, query, all_qs=False, append=True)

all_qs=True 一次污染所有url
append=True 追加payload
```

### 使用
```
# Configuration Payload
payloads = ['phpinfo();', 'echo 1;']

# Configuration URL or QueryString
url = 'http://127.0.0.1/?a=1&b=2'

p = URLPollution(payloads)
print p.payload_generator(url, append=False)
print p.payload_generator(url, all_qs=True, append=False)
```

```
['http://127.0.0.1/?a=phpinfo%28%29%3B&b=2', 'http://127.0.0.1/?a=1&b=phpinfo%28%29%3B', 'http://127.0.0.1/?a=echo+1%3B&b=2', 'http://127.0.0.1/?a=1&b=echo+1%3B']
['http://127.0.0.1/?a=phpinfo%28%29%3B&b=phpinfo%28%29%3B', 'http://127.0.0.1/?a=echo+1%3B&b=echo+1%3B']
```


