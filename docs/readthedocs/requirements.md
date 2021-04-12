
# 分离文档工程和代码工程的requirements.txt

默认情况下，`readthedocs`会使用`root`路径下的`requirements.txt`进行编译环境构建

## 问题

编译时出现如下错误:

```
ERROR: No matching distribution found for...
```

## 解决

查询编译日志时发现是代码工程使用的依赖无法下载安装导致的。`readthedocs`给出了提示，使用`.readthedocs.yml`文件指定文档工程依赖文件。在根目录下新建文件`.readthedocs.yml`，输入如下内容：

```
# .readthedocs.yaml
# Read the Docs configuration file
# See https://docs.readthedocs.io/en/stable/config-file/v2.html for details

# Required
version: 2

mkdocs:
  configuration: mkdocs.yml

# Optionally set the version of Python and requirements required to build your docs
python:
   version: 3.7
   install:
   - requirements: docs/requirements.txt
```

这样就指定了使用`docs/requirements.txt`文件进行环境构建。更多的选项参考[Configuration File V2](https://docs.readthedocs.io/en/stable/config-file/v2.html#python)