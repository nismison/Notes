# uniapp 如何禁止或监听默认返回事件

页面生命周期有个 onBackPress 方法，可以监听返回事件

onBackPress(event) 返回 event ={form: backbutton | navigateBack}

- Android 实体返回键 (from = backbutton)
- 顶部导航栏左边的返回按钮 (from = backbutton)
- 返回 API，即 uni.navigateBack() (from = navigateBack)

**注意事项：**

- 只有在该函数中返回值为 true 时，才表示不执行默认的返回，自行处理此时的业务逻辑。
- 不返回或返回其它值，均会执行默认的返回行为。
- H5平台，顶部导航栏返回按钮支持 onBackPress()，浏览器默认返回按键及Android手机实体返回键不支持
- onBackPress() 暂不支持直接在自定义组件中配置该函数，目前只能是在页面中来处理。

**具体用法：**

```js
onBackPress(e) {  
	// 这里可以自定义返回逻辑，比如下面跳转其他页面
	uni.switchTab({
		url: '/pages/tabBar/mine/mine'
	})
	// return true 表示禁止默认返回事件
	return true
}
```

