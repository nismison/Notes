## 上传图片

```js
/**
 * 上传图片
 */
const uploadFile = () => {
  const fileChooser = document.createElement('input');
  fileChooser.accept = "image/png,image/gif,image/jpeg,image/x-icon";
  fileChooser.type = 'file';
  fileChooser.click();
  fileChooser.addEventListener('change', function () {
    const filesList = fileChooser.files;
    if (filesList.length) { //如果取消上传，则该文件的长度为0
      encodeBase64(fileChooser).then(res => {
        const imgBase64 = res
        // ...
      })
    }
  })
}
```



## 转base64编码

```js
/**
 * 图片转base64
 * @param params 目标icon地址(可以为base64编码)
 */
const encodeBase64 = (params) => {
  // 上传图片转base64
    return new Promise(resolve => {
      // 生成一个文件读取的对象
      const reader = new FileReader();
      reader.onload = ev => {
        resolve(ev.target.result) // base64
      }
      //发起异步读取文件请求，读取结果为data:url的字符串形式，
      reader.readAsDataURL(params.files[0]);
    })
}
```

