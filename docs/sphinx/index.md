
# 引言

[SPHINX](http://www.sphinx-doc.org/en/master/)是一个文档生成工具，可用于多种语言，有以下特性：

1. 输出格式：生成文档可以是`HTML、LaTex、ePub、Textinfo、manual pages、plain text`
2. 强大的互参考功能：用于函数、类、引文、词汇术语和相似信息的语义标记和自动链接
3. 层次结构：文档树的简单定义，自动链接到同级，父类和子类节点
4. 自动索引：通用索引以及语言特定的模块索引
5. 代码处理：使用`Pygments`高亮器实现自动高亮
6. 扩展功能：代码片段的自动测试，包括来自`Python`模块（`API`文档）的文档字符串，以及更多
7. 贡献扩展：超过`50`个扩展包被用户发布在另一个仓库，其中的大多数可以通过`PyPI`安装

默认情况下，`sphinx`使用`reStructuredText`语言作为标记语言，它也支持`markdown`(需要设置)

## 安装

`sphinx`提供了多种安装方式，常用`Python`安装方式：

    pip install -U Sphinx

*升级`sphinx`同样使用此命令*

当前使用版本：

```
$ sphinx-quickstart --version
sphinx-quickstart 2.2.1
```

## 相关阅读

* [Installing Sphinx](http://www.sphinx-doc.org/en/master/usage/installation.html)