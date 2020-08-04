# Mac自定义命令/脚本



## 一、修改命令别名

1、编辑 `~/.bashrc` 文件，将需要执行的别名命令添加到这个文件末尾

```shell
vim ~/.bashrc
# 添加别名
alias md=mkdir
```

然后退出保存，执行 `source ~/.bashrc` 使刚才的配置生效

2、编辑 `~/.bashrc` 文件，在文件末尾加入一行

```shell
source ~/.bashrc
```

同样的，退出保存后执行 `source ~/.bash_profile` 使刚才的配置生效就可以了。

------

**如果终端安装了zsh，上面的配置不一定生效，需要在 `~/.zshrc` 文件中配置**

```shell
vim ~/.zshrc
# 添加别名
alias md=mkdir
```

退出保存后执行 `source ~/.zshrc` 使刚才的配置生效就OK了。



## 二、自定义脚本Shell

1、创建自己的shell脚本文件夹，并创建脚本文件`testcc.sh`

```shell
mkdir ~/mycmd
touch testcc.sh
```

2、给文件夹下所有sh文件添加权限

```shell
chmod u+x *.sh
```

3、编辑 `~/.bash_profile` 更改PATH变量

```shell
vim ~/.bash_profile
# 添加PATH变量
export PATH=$PATH:~/mycmd
```

4、保存退出，执行 `source ~/.bash_profile`

5、**如果终端安装了zsh，终端重启后需要重新执行 `source ~/.bash_profile `命令才会生效，所以需要配置 `~/.zshrc`文件**

```shell
vim ~/.zshrc
# 最后一行添加
source ~/.bash_profile
```

6、重启终端，输入testcc.sh即可运行自定义脚本，如果不喜欢输入扩展名，可以设置对应的alias