## 检测手机号码格式

```js
/**
 * 检测手机号码格式
 * @param str 原始字符串
 * @returns {boolean}
 */
export const isMobile = (str) => {
	return /^1(3|4|5|6|7|8|9)\d{9}$/.test(str);
}
```

