---
title: "Python3笔记"
date: 2022-02-08T02:55:20+08:00
lastmod: 2020-03-10T01:39:00+08:00
draft: false
tags: [python,笔记]
categories: [学习资料]
---
## 介绍
> Python3 是一种解释性的、可交互的、面向对象的编程语言<!--more-->
- 运行环境ubuntu
## 安装Python
1. 首先是更新源
`sudo apt update`
2. 然后安装Python
`sudo apt install python3`
3. 最后升级Python
`sudo apt upgrade python3`
4. python3在哪里？
`whereis python3`
5. 可执行的这个东西到底在哪？
`which python3`
## Python命令
### 运行和退出Python
- `python3`运行Python
- `quit()`或`ctrl+d`退出Python
### print函数：输出
`print("Hello world",sep='参数间的间隔，默认为一个空格',end='后缀，默认\n，即换行')`
- 括号内为参数，参数可为多个，用逗号,隔开
    ```python
    >>>print("a",chr("a"))
    a 97
    ```
{{< admonition tip >}}
1. 函数后均需加一对[`()`]^(圆括号)，字符串要用一对英文引号引起，[`""`]^(双引号)和[`''`]^(单引号)均可。
2. 字符串可使用乘法，如
```python
>>>print("Hello world"*10)
Hello worldHello worldHello worldHello worldHello worldHello worldHello worldHello worldHello worldHello world
```
{{< /admonition >}}
### 查看py文件
`cat name.py`
### 运行py文件
`python3 name.py`
- python3 是我们执行的解释器程序
- name.py 是 python3 的参数
### 下载一个别人编好的程序
`wget https://labfile.oss.aliyuncs.com/courses/1330/game.py`
- 用python3解释game.py
`python3 game.py`
### python's debugger
`python3 -m pdb name.py`
或者使用
`pdb3 name.py`

运行之后
- `h` 查询 help 帮助
- `l` 进行 list 列表
- `n` 进行 next 向下执行
- `q` 执行 quit 退出

### Unicode序数互换
```python
>>>ord("h")
104
>>>chr(104)
'h'
```
### 进制转换
进制格式
- [二进制]^(binary)：0b开头，如：0b1100001
- [八进制]^(octal)：0o开头，如：0o141
- [十进制]^(integer)：纯数字，如：97
- [16进制]^(hexadecimal)：0x开头，如：0x61
```python
# 转为二进制
>>>bin(97)
'0b1100001'

# 转为八进制
>>>oct(97)
'0o141'

# 转为十进制
>>>int(0x61)
97

# 转为16进制
>>>hex(97)
'0x61'
```
### 编码、解码
```python
# [字符串]^(str)'a'[编码]^(encode)之后为[字节]^(byte)b'\x61'
>>>"a".encode("ascii")
b'\x61'

>>>b'\x61'
b'a'

# [字节]^(byte)b'\x61'[解码]^(decode)之后为[字符串]^(str)'a'
>>>b'\x61'.decode("ascii")
'a'
```
### 换行字符`\n`
```python
>>>ord(\n)
10
```
`10`在[ascii]^(American Standard Code for Information Interchange)码表中对应[LF]^(Line Feed)
```python
>>>print("Hello\nworld")
Hello
world

# 反向操作
>>>print("Hello"+chr(10)+"world")
Hello
world
```
### import
```python
# 导入一个名为time的[模块包]^(module)
>>>import time 
```
{{< admonition tip >}}
如`time`这样的外置函数需要`import`后才能使用，下面是一些内置函数：
- help()
- int()
- chr()
- bin()
- hex()
- ord()
- print()
{{< /admonition >}}
### time模块包
```python
# 得到的是一个浮点数，也就是当前时间距1970年1月1日00:00的秒数，称为时间戳
>>>time.time()

# 使用该函数可将时间戳转换为时间元组
>>>time.localtime()

# 将时间元组转换为可读的ascii字符串
>>>time.asctime()
```
{{< admonition tip >}}
`[time]^(模块包名).[time()]^(函数名)`中，前面的`time`是模块包名，后面的`time()`为函数名
{{< /admonition >}}
{{< admonition note "应用" false>}}
```python
# 引入一个包叫time
>>>import time

# 得到当前时间的asctime形式字符串
>>>localtime = time.asctime(time.localtime(time.time()))

# 进行输出
>>>print ("本地时间为 :", localtime)
```
{{< /admonition >}}

## vim使用方法
### 使用vim打开文件
`vi name.py`或`vim name.py`

- 分窗口分别打开文件
`vim -o name1.py name2.py`
### 快捷键
- `i`键进入编辑，`Esc`键退出编辑
- `o`键进入编辑并将光标移至下一行开头
- `gg`将光标移动回到最开头
- `yG`从当前位置复制到结尾
- `2P`粘贴 2 次
- `G`到最后一行

### vim内部指令
- `:`进入命令行模式
- `:q`退出，`:q!`强制退出
- `:w`写入(保存)

{{< admonition tip >}}
命令可按顺序组合使用

如`:wq`保存并退出
{{< /admonition >}}
- `:!`可执行外部命令
- 使用`%`代表当前文件
- `:!python3 %`用python3运行当前文件
- `:w|!python3 %`保存并用python3运行当前文件
- `|`意思是把命令联合起来依次执行
- `:%!xxd`查看这个文件的二进制形态
- `:%!xxd –r`恢复
- `%`是指的对于所有行的范围
- `xxd`指的是转化为 16 进制形式