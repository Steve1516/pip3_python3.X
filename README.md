
pip3_python3.X
================

how to install pip3 for python3.x
------------------------------------

#一、先安装python3 

安装python3.x 这里不多赘述，so easzy！！

##1、先到官方网站下载python3的安装包

https://www.python.org/downloads/source/  －－－我下载的是Python-3.5.2.tar.xz

##2、上传包到服务器

##3.解压

```Bash
tar -xf Python-3.5.2.tar.xz  

##4.编译安装

！！！！注意 注意 ⚠️  在编译之前需要安装一些必须的依赖，否则当报错的时候还得重新编译 －－－（我就是吃了这个亏，千万要注意奥。。。）

安装必要依赖（至少需要如下两个，我个人就遇到如下两个）

yum install openssl-devel   -y

yum install zlib-devel  -y

好了现在可以安心的编译咯：

cd Python-3.5.2
./configure --prefix=/opt/Python     #安装目录可以自己定义无所谓。
make
make install

编译完成后会在如 /opt/下生成Python的文件夹 ，没错这就是编译完成的python  －－为了方便之行小伙伴们可以自己定义一个软连接如下：

# ln -s /opt/Python/bin/python3 /usr/bin/python3

这样就可以直接食用python3了如下：

　　　　　　　　　　

好到目前为止，我们在linux下安装python3的任务已经完成，下面进入关键的地方，给python3安装pip3

二.install pip for python3.x

其实这也不难。。下载量个包，执行两个命令搞定。

1.首先安装setuptools

　　小伙伴们可以通过官方模块库来下载：https://pypi.python.org/pypi

　　这里我就直接用wget到服务器上下载了版本为19.6（小伙伴们可以尝试新的版本奥。。）
复制代码

wget --no-check-certificate  https://pypi.python.org/packages/source/s/setuptools/setuptools-19.6.tar.gz#md5=c607dd118eae682c44ed146367a17e26

tar -zxvf setuptools-19.6.tar.gz

cd setuptools-19.6.tar.gz

python3 setup.py build

python3 setup.py install

复制代码

2.然后直接安装pip就搞定了。。

　　同样先下载然后在执行命令搞定！！
复制代码

wget --no-check-certificate  https://pypi.python.org/packages/source/p/pip/pip-8.0.2.tar.gz#md5=3a73c4188f8dbad6a1e6f6d44d117eeb

tar -zxvf pip-8.0.2.tar.gz

cd pip-8.0.2

python3 setup.py build

python3 setup.py install

复制代码

安装完成之后我们再来看下python的bin目录下都有什么东西吧

哈哈。。通过以上我们已经给python3安装好了 pip3了。。。（小伙伴们也可以做个软连接，来方便实用奥。。）

 
三。来做个测试吧

1.首先我们进入pytho3
复制代码

[root@centos3 bin]# python3
Python 3.5.2 (default, Jul 27 2016, 03:36:56) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-4)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pymysql
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'pymysql'   ##没有此模块奥
>>> 

复制代码

好 ，我们用新安装的pip3来装下试试：
复制代码

[root@centos3 bin]# /opt/Python/bin/pip3 install pymysql
Collecting pymysql
  Downloading PyMySQL-0.7.5-py2.py3-none-any.whl (77kB)
    100% |████████████████████████████████| 81kB 3.2kB/s 
Installing collected packages: pymysql
Successfully installed pymysql-0.7.5

######安装完成

复制代码

安装完成了，看来pip3本身没有问题，我们测试下是否真正的给python3装上了这个模块吧（有可能装到了python2上了呢 ……-_-#）
复制代码

[root@centos3 bin]# python3
Python 3.5.2 (default, Jul 27 2016, 03:36:56) 
[GCC 4.4.7 20120313 (Red Hat 4.4.7-4)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pymysql
>>> 

复制代码

哈哈哈 ok了。。 结束！！

 