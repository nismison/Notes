## 字典加密、解密

```python
import pickle
import base64


def dict_dumps_2_string(json_dict):
    """
    字典加密为字符串
    :param json_dict: 需要加密的字典
    :return 加密后的字符串
    """
    json_bytes = pickle.dumps(json_dict)
    # 加密
    json_secret = base64.b64encode(json_bytes)
    # 转字符串
    json_str = json_secret.decode()

    return json_str


def string_load_2_dict(json_str):
    """
    字符解密为字典
    :param json_str: 需要解密的字符串
    :return 解密后的字典
    """
    json_secret = json_str.encode()
    # 解密
    json_bytes = base64.b64decode(json_secret)
    # 转字典
    json_dict = pickle.loads(json_bytes)

    return json_dict
```

------

## 字符串加密、解密

```python
def encrypt_string(message):
    """
    字符串加密
    :param message: 需要加密的字符串
    :return 加密后的字符串
    """
    encode_result = ""
    for char in message:
        char_int = ord(char)
        if char.isalpha():  # 判断是否为字母
            if 64 < char_int < 78 or 96 < char_int < 110:  # 针对其中的部分字母进行加密
                encode_result += "00" + str((char_int + 13) * 2) + "|"
            else:  # 对剩下字母进行加密
                encode_result += "01" + str(char_int - 23) + "|"

        elif '\u4e00' <= char <= '\u9fff':  # 单个汉字可以这么判断
            encode_result += "02" + str(char_int + 24) + "|"
        else:  # 对数字、特殊字符进行加密
            encode_result += "03" + str(char_int) + "|"

    return encode_result


def decrypt_string(message):
    """
    字符串解密
    :param message: 需要解密的字符串
    :return 解密后的字符串
    """
    decode_result = ""

    # 将message转换为list
    message_list = message.split("|")
    message_list.remove("")  # 移除list中的空元素

    for i in message_list:
        type_ = i[:2]
        char_number = int(i[2:])
        if type_ == "00":
            char_number = int(char_number / 2 - 13)
        elif type_ == "01":
            char_number = char_number + 23
        elif type_ == "02":
            char_number = char_number - 24
        else:
            char_number = char_number

        decode_result += chr(char_number)

    return decode_result
```

