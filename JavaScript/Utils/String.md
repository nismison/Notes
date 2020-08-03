## 去除字符串中所有的空格以及换行符

```js
/**
 * 去除字符串中所有的空格以及换行符
 * @param str 原始字符串
 * @returns {String}
 */
export const trim = str => {
	return str.replace(/\ +/g,"").replace(/[\r\n]/g,"")
}
```

------

## 判断字符串中是否全是中文

```js
/**
 * 判断字符串中是否全是中文
 * @param str 原始字符串
 * @returns {Boolen} false为不全是中文，true为全是中文
 */
export const isChn = str => {
	const reg=/^[\u4E00-\u9FA5]+$/;
	if(!reg.test(str)){
		// 不全是中文
		return false
	}
	// 全是中文
	return true
}
```

------

## 手机号码中间换成星号

```js
/**
 * 手机号码中间换成****
 * @param phone
 * @returns {string}
 */
export const formatMobile = (phone) => {
	if (count(phone) === 0) {
		return "";
	}
	return phone.substring(0, 3) + "****" + phone.substring(phone.length - 4);
}
```

------

## 邮箱中间换成星号

```js
/**
 * 邮箱中间换成****
 * @param email 原始邮箱地址
 * @returns {string}
 */
export const formatEmail = (email) => {
	if (count(email) === 0) {
		return "";
	}
	const str = email.split('@')
	let _s = '';
	if (str[0].length > 3) {
		for (var i = 0; i < str[0].length - 3; i++) {
			_s += '*';
		}
	}
	return str[0].substr(0, 3) + _s + '@' + str[1];
}
```

------

## 字符串是否包含

```js
/**
 * 字符串是否包含
 * @param string 原始字符串
 * @param find 需要查找的字符串
 * @returns {boolean}
 */
const strExists = (string, find) => {
	string += "";
	find += "";
	return (string.indexOf(find) !== -1);
}
```

------

## 字节转换

```js
/**
 * 字节转换
 * @param bytes
 * @returns {string}
 */
export const bytesToSize = (bytes) => {
	if (bytes === 0) return '0 B';
	let k = 1024;
	let sizes = ['B', 'KB', 'MB', 'GB', 'TB', 'PB', 'EB', 'ZB', 'YB'];
	let i = Math.floor(Math.log(bytes) / Math.log(k));
	if (typeof sizes[i] === "undefined") {
		return '0 B';
	}
	return runNum((bytes / Math.pow(k, i)), 2) + ' ' + sizes[i];
}
```

------

## 随机字符

```js
/**
 * 随机字符
 * @param len 字符长度
 * @returns {string}
 */
const randomString = (len) => {
	len = len || 32;
	let chars = 'ABCDEFGHJKMNPQRSTWXYZabcdefhijkmnprstwxyz2345678oOLl9gqVvUuI1';
	let maxPos = chars.length;
	let str = '';
	for (let i = 0; i < len; i++) {
		str += chars.charAt(Math.floor(Math.random() * maxPos));
	}
	return str;
}
```

------

## 补零

```js
/**
 * 补零
 * @param str 原始字符串
 * @param length 字符串长度
 * @param { boolen } after 是否在字符串后面加零
 * @returns {*}
 */
const zeroFill = (str, length, after) => {
	str += "";
	if (str.length >= length) {
		return str;
	}
	let _str = '',
		_ret = '';
	for (let i = 0; i < length; i++) {
		_str += '0';
	}
	if (after || typeof after === 'undefined') {
		_ret = (_str + "" + str).substr(length * -1);
	} else {
		_ret = (str + "" + _str).substr(0, length);
	}
	return _ret;
}
```

