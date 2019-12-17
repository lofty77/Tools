原文链接：http://linux.vbird.org/linux_basic/0320bash.php


## 环境变量的功能
使用 `env` 查看环境变量，常见的环境变量说明：
* HOME 代表用户的家目录
* USER 代表当前用户
* PATH 代表可执行文件的搜索路径
* SHELL 代表当前 shell 环境的版本
* LANG 代表当前 shell 环境的语言


# bash 的操作环境


## bash 的环境配置文件
在开始介绍 bash 的配置文件之前，需要先介绍 login shell 与 non-login shell。因为 login shell 与 non-login shell 读取的配置文件是不相同的。
* login shell：获取 bash 时需要完整的登录流程，称为 login shell，它会读取 /etc/profile 系统级别的配置文件和 ~/.bash_profile 或 ~/.bash_login 或 ~/.profile 三个用户级别的配置文件中的一个。
* non-login shell：获取 bash 时不需要重复的登录流程，称为 non-login shell，它仅会读取 ~/.bashrc 配置文件。

## 用户环境变量

```
~/.bashrc
```


## 系统环境变量
```
/etc/profile
```

