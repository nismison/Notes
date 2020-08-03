## 获取数组最后一个值

```js
/**
 * 获取数组最后一个值
 * @param array 数组
 * @returns {*}
 */
const last = (array) => {
	let str = false;
	if (typeof array === 'object' && array.length > 0) {
		str = array[array.length - 1];
	}
	return str;
}
```

------

## 删除数组最后一个值

```js
/**
 * 删除数组最后一个值
 * @param array 数组
 * @returns {Array}
 */
const delLast = (array) => {
	let newArray = [];
	if (typeof array === 'object' && array.length > 0) {
		each(array, (index, item) => {
			if (index < array.length - 1) {
				newArray.push(item);
			}
		});
	}
	return newArray;
}
```

------

## 去除数组中的非数字项

```js
/**
 * 去除数组中的非数字项
 * @param value 原始数组
 * @returns {Array}
 */
export const removerNumberNaN = (...value) => {
	let array = [];
	value.forEach((ele) => {
		if (!isNaN(Number(ele))) {
			array.push(ele);
		}
	});
	return array;
}
```

------

## 克隆对象

```js
/**
 * 克隆对象
 * @param myObj 原始对象
 * @returns {*}
 */
export const clone = (myObj) => {
	if (typeof(myObj) !== 'object') return myObj;
	if (myObj === null) return myObj;
	//
	if (likeArray(myObj)) {
		let [...myNewObj] = myObj;
		return myNewObj;
	} else {
		let { ...myNewObj
		} = myObj;
		return myNewObj;
	}
}
```

------

## 传入指定长度生成随机数组

```js
/**
 * 传入指定长度生成随机数组
 * @param length 数组长度
 * @returns Array
 */
export default randomArray = length => {
    let i = 0
    let index = 0
    let temp = null
    let arr = [length]
    length = typeof(length) === 'undefined' ? 9 : length
    for(i=1; i<=length; i++) {
        arr[i - 1] = i
    }
    for(i = 1; i<=length; i++) {
        index = window.parseInt(Math.random() * (length - i)) + i
        if (index != i) {
        temp = arr[i-1]
        arr[i-1] = arr[index-1]
        arr[index-1] = temp
        }
    }
    return arr
}
```

