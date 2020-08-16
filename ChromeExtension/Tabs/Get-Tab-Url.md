## 获取当前Tab的Url

```js
/*
 * 获取当前Tab的Url
 */
const getCurTabUrl = () => {
  chrome.tabs.query({
    active: true,
    lastFocusedWindow: true
  }, function (tabs) {
    let url = tabs[0].url;
    // ... Do something here
  })
}
```

