## 千分法

```js
/**
 * 千分法
 * @param num 原始数字
 * @returns {string}
 */
export const toThousands = (num) => {
	let str = num.toString(),
		res = ''
	if (num < 100) return num
	const reg = /(?=(\B)(\d{3})+$)/g
	const decimal = str.split('.')
	if (decimal.length >= 2) {
		res = '.' + decimal[1]
	}
	return decimal[0].replace(reg, ',') + res
}
```

