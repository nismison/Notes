## 计算YYYY-MM-DD格式的两个日期天数差

```js
/**
 * 计算YYYY-MM-DD格式的两个日期天数差
 * @param startTime 开始时间
 * @param endTime 结束时间
 * @param diffType 见switch
 * @returns {Int} 相差天数
 */
export const GetDateDiff = (startTime, endTime, diffType = 'day') => {
	//将xxxx-xx-xx的时间格式，转换为 xxxx/xx/xx的格式 
	startTime = this.form.checkInTime.replace(/\-/g, "/");
	endTime = this.form.checkOutTime.replace(/\-/g, "/");

	//将计算间隔类性字符转换为小写
	diffType = diffType.toLowerCase();
	var sTime = new Date(startTime); //开始时间
	var eTime = new Date(endTime); //结束时间
	//作为除数的数字
	var divNum = 1;
	switch (diffType) {
		case "second":
			divNum = 1000;
			break;
		case "minute":
			divNum = 1000 * 60;
			break;
		case "hour":
			divNum = 1000 * 3600;
			break;
		case "day":
			divNum = 1000 * 3600 * 24;
			break;
		default:
			break;
	}
	return parseInt((eTime.getTime() - sTime.getTime()) / parseInt(divNum));
}
```

------

## 时间戳转yyyy-MM-dd hh:mm:ss

```js
/**
 * 时间戳转时间格式
 * @param timestamp
 * @param fmt
 * @returns {string}
 */
export const formatDate = (timestamp = null, fmt = 'yyyy-mm-dd h:M:s') => {
	// 其他更多是格式化有如下:
	// yyyy:mm:dd|yyyy:mm|yyyy年mm月dd日|yyyy年mm月dd日 hh时MM分等,可自定义组合
	if (!timestamp) return '--'
	timestamp = parseInt(timestamp);
	// 如果为null,则格式化当前时间
	if (timestamp == null) timestamp = Number(new Date());
	// 判断用户输入的时间戳是秒还是毫秒,一般前端js获取的时间戳是毫秒(13位),后端传过来的为秒(10位)
	if (timestamp.toString().length == 10) timestamp *= 1000;
	let date = new Date(timestamp);
	let ret;
	let opt = {
		"y+": date.getFullYear().toString(), // 年
		"m+": (date.getMonth() + 1).toString(), // 月
		"d+": date.getDate().toString(), // 日
		"h+": date.getHours() < 10 ? '0' + date.getHours(): date.getHours().toString(), // 时
		"M+": date.getMinutes() < 10 ? '0' + date.getMinutes(): date.getMinutes().toString(), // 分
		"s+": date.getSeconds() < 10 ? '0' + date.getSeconds(): date.getSeconds().toString() // 秒
		// 有其他格式化字符需求可以继续添加，必须转化成字符串
	};
	for (let k in opt) {
		ret = new RegExp("(" + k + ")").exec(fmt);
		if (ret) {
			fmt = fmt.replace(ret[1], (ret[1].length == 1) ? (opt[k]) : (opt[k].padStart(ret[1].length, "0")))
		};
	};
	return fmt;
}
```

```js
/**
 * 时间戳转yyyy-MM-dd hh:mm:ss
 * @param time 需要转换的时间戳
 * @returns {string}
 */
filtersTime(time = +new Date()) {
    let date = new Date(time + 8 * 3600 * 1000);
    return date
        .toJSON()
        .substr(0, 19)
        .replace('T', ' ')
        .replace(/-/g, '-');
}
```

------

## 时间戳转几天前、几小时前、几天前等

```js
/**
 * 时间戳转几天前、几小时前、几天前等
 * @param dateTimeStamp 时间戳
 * @returns {string}
 */
export const getDateDiff = dateTimeStamp => {
	const minute = 1000 * 60
	const hour = minute * 60
	const day = hour * 24
	const halfamonth = day * 15
	const month = day * 30
	const now = new Date().getTime()
	const diffValue = now - dateTimeStamp
	if(diffValue < 0) return
	const monthC = diffValue / month
	const weekC = diffValue / (7 * day)
	const dayC = diffValue / day
	const hourC = diffValue / hour
	const minC = diffValue / minute
	let result = ""
	if (monthC >= 1){
		result = "" + parseInt(monthC) + "月前"
	}else if (weekC >= 1){
		result = "" + parseInt(weekC) + "周前"
	}else if (dayC >= 1){
		result = ""+ parseInt(dayC) + "天前"
	}else if (hourC >= 1){
		result = ""+ parseInt(hourC) + "小时前"
	}else if (minC >= 1){
		result = ""+ parseInt(minC) + "分钟前"
	}else {
		result = "刚刚"
	}
	return result
}
```

