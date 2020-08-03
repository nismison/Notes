# 前端开发约定

## 目录：
> * [命名规范](#name)
> * [模块划分](#module)
> * [防止嵌套过深](#hierarchy)
> * [开发约定示例](https://github.com/wasdokij/css/blob/master/README.md)
> * [JS编码规范](https://github.com/yuche/javascript)
> * [补充部分](#replenish)

---
### 规范关键词

##### 常见class关键词：
 ```
布局类：header, footer, container, main, content, aside, page, section
包裹类：wrap, inner
区块类：region, block, box
结构类：hd, bd, ft, top, bottom, left, right, middle, col, row, grid, span
列表类：list, item, field
主次类：primary, secondary, sub, minor
大小类：s, m, l, xl, large, small
状态类：active, current, checked, hover, fail, success, warn, error, on, off
导航类：nav, prev, next, breadcrumb, forward, back, indicator, paging, first, last
交互类：tips, alert, modal, pop, panel, tabs, accordion, slide, scroll, overlay,
星级类：rate, star
分割类：group, seperate, divider
等分类：full, half, third, quarter
表格类：table, tr, td, cell, row
图片类：img, thumbnail, original, album, gallery
语言类：cn, en
论坛类：forum, bbs, topic, post
方向类：up, down, left, right
其他语义类：btn, close, ok, cancel, switch; link, title, info, intro, more, icon; form, label, search, contact, phone, date, email, user; view, loading...
 ```

### 模块划分

 以页面分成模块然后以一个单词来名，模块下的组件(模块+组件)的命名方式，姓氏命名法（祖姓 + 名），如下图  如：

```css
.header { }
.header > .header-button { }
```

### 防止嵌套过深

约定好全局公共模块命名，如

```css
.tb{ }// 淘宝
.tb-xxx{ }// 淘宝-xxx
```

在子孙模块数量可预测的情况下，严格继承祖先模块的命名前缀,要是子模块不多的时候就要写全。

```html
<div class="modulename">
    <div class="modulename-cover"></div>
    <div class="modulename-info"></div>
</div>
```

当子孙模块超过`4级`或以上的时候，可以考虑在祖先模块内具有识辨性的独立缩写作为新的子孙模块

```html
<div class="modulename">
    <div class="modulename-cover"></div>
    <div class="modulename-info">
        <div class="modulename-info_user">
            <div class="modulename-info-user-img">
                <img src="" alt="">
                <!-- 这个时候 miui 为 modulename-info-user-img 首字母缩写-->
                <div class="miui-tit"></div>
                <div class="miui-txt"></div>
                ...
            </div>
        </div>
        <div class="modulename-info-list"></div>
    </div>
</div>
```
