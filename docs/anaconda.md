## linux 环境下安装
###  下载
 - [官网](https://www.anaconda.com/distribution/)
###  安装
```bash
bash Anaconda3-2019.07-Linux-x86_64.sh
```
### 设置环境变量
打开  ~/.bashrc . 配置参考如下
```bash
export JAVA_HOME=/usr/jdk8/jdk1.8.0_181/
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export SCRAPE=/home/liang.liang/code/lianjia-beike-spider
export ANACONDA=/home/pyuser/anaconda3
export PATH=${ANACONDA}/${SCRAPE}/${JAVA_HOME}/bin:$PATH
```
### 激活环境变量
```linux
source ~/.bashrc
```
### 验证安装成功
```linux
liang.liang@ubuntu:~/Downloads$ python
Python 3.7.4 (default, Aug 13 2019, 20:35:49) 
[GCC 7.3.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
### 启动Anaconda Navigator图形化界面
```linux
$ conda install -c anaconda anaconda-navigator​
$ anaconda-navigator
```
