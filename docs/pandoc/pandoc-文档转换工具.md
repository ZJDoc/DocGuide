
# [Pandoc]文档转换工具

[Pandoc](https://pandoc.org/)是一个通用的文档转换器

## 安装

下载[pandoc](https://github.com/jgm/pandoc/releases)并安装

```
sudo dpkg -i pandoc*.deb
sudo apt-get install -f 
```

## 测试

```
$ pandoc -v
pandoc 1.19.2.1
Compiled with pandoc-types 1.17.0.4, texmath 0.9, skylighting 0.1.1.4
Default user data directory: /home/zj/.pandoc
Copyright (C) 2006-2016 John MacFarlane
Web:  http://pandoc.org
This is free software; see the source for copying conditions.
There is no warranty, not even for merchantability or fitness
for a particular purpose.
```

## 格式转换

`pandoc`支持许多标记语言之间的转换，比如`markdown`、`json`、`html`、`lua`、`reStructuredText`等等

![](./imgs/diagram.jpg)

目前比较关心的是`markdown`和`rst`之间的转换，使用如下命令

```
pandoc test.md -f markdown -t rst -s -o test1.rst
```

* `test.md`是源文件
* `-f`表示源文件格式
* `-t`表示结果文件格式
* `-s`表示生成独立文件
* `-o`表示结果文件名

经过测试发现确实有用，能够部分解决`sphinx`中`markdown`数学公式和表格的渲染问题

## 相关阅读

* [文件格式转换神器-pandoc](https://www.cnblogs.com/yinghao1991/p/6535911.html)