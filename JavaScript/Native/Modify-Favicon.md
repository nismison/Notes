## 动态修改页面favicon

```js
/**
 * 修改页面favicon
 * @param iconUrl 目标icon地址(可以为base64编码)
 */
const setTabIcon = iconUrl => {
  // 删除原有icon
	let links = document.querySelectorAll("link[rel*='icon']");
	links.forEach(node => {
		node.parentNode.removeChild( node )
	})
  // 新增icon
	let link = document.createElement('link');
	link.type = 'image/x-icon';
	link.rel = 'shortcut icon';
	link.href = iconUrl;
	document.getElementsByTagName('head')[0].appendChild(link);
}
```

