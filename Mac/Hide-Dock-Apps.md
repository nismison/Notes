## 一、terminal进入App包

```shell
# 以Panda.app为例
cd /Applications/Panda.app/Contents
```

------

## 二、编辑Info.plist

```shell
vim Info.plist
# 或者
vi Info.plist
```

------

## 三、在dict标签中添加以下内容

```
<key>LSUIElement</key>
<true/>
```

------

## 四、重启应用，如果图标还在，则右击选择“从程序坞中移除”