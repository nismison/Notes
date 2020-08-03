## 生成随机字符串

```python
def ran_str(num):
    """
    生成随机字符串
    :param num: 字符串长度
    :return 随机字符串
    """
    H = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'
    salt = ''
    for i in range(num):
        salt += choice(H)

    return salt
```

