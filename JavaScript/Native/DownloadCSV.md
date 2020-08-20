## 下载CSV文件

```js
/**
 * 下载CSV文件
 * @param fileName 保存文件名称
 * @param head { Array } 表头(一个元素一列)
 * @param content { Array } 内容(一个元素一行，行内使用 "," 分隔列)
 * @returns { * }
 */
export const downloadCsv = (fileName, head, content) => {
  const headStr = head.join(',');
  const contentStr = content.join('\n');
  const aTag = document.createElement('a');
  const csvData = "data:text/csv;charset=utf-8,\ufeff" + headStr + '\n' + contentStr
  aTag.download = fileName;
  aTag.href = csvData;
  aTag.click();
}
```

