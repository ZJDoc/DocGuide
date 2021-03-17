
# 编译问题

## 问题一：编译`conf.py`文件时，发生中文格式问题

参考：

[解决UnicodeDecodeError: 'ascii' codec can't decode byte 0xe5 in position 108: ordinal not in range(128](https://blog.csdn.net/lengyuewusheng99/article/details/52822450)

[Python3异常-AttributeError: module 'sys' has no attribute 'setdefaultencoding'](https://blog.csdn.net/fly910905/article/details/74922378)

编译`conf.py`文件时，发生中文格式问题

    Running Sphinx v1.7.9
    WARNING: the config value 'epub_title' is set to a string with non-ASCII characters; this can lead to Unicode errors occurring. Please use Unicode strings, e.g. u'Content'.
    WARNING: the config value 'project' is set to a string with non-ASCII characters; this can lead to Unicode errors occurring. Please use Unicode strings, e.g. u'Content'.
    loading translations [en]... done
    making output directory...

    ...
    ...
    UnicodeDecodeError: 'ascii' codec can't decode byte 0xe5 in position 0: ordinal not in range(128)

    Encoding error:
    'ascii' codec can't decode byte 0xe5 in position 0: ordinal not in range(128)
    The full traceback has been saved in /tmp/sphinx-err-VIWOpI.log, if you want to report the issue to the developers.

有两种解决方法：

第一种是针对`python2`，在`conf.py`中如下代码，将编码格式改为`utf-8`

    import sys 
    reload(sys) 
    sys.setdefaultencoding('utf8')

第二种是修改`readthedocs`编译环境，在`Admin->Advanced Settings->Python interpreter:`

将选项修改成`CPython 3.x`

## 问题二：`pdflatex`编译出错

编译过程中运行`pdflatex`时出错:

    pdflatex -interaction=nonstopmode /home/docs/checkouts/readthedocs.org/user_builds/zj-computer-foundation/checkouts/latest/docs/source/_build/latex/sphinx.tex

出错提示:

    This is pdfTeX, Version 3.14159265-2.6-1.40.16 (TeX Live 2015/Debian) (preloaded format=pdflatex)
    restricted \write18 enabled.
    entering extended mode
    (/home/docs/checkouts/readthedocs.org/user_builds/zj-computer-foundation/checko
    uts/latest/docs/source/_build/latex/sphinx.tex
    LaTeX2e <2016/02/01>
    Babel <3.9q> and hyphenation patterns for 81 language(s) loaded.
    ...
    ...    
    (/usr/share/texlive/texmf-dist/tex/generic/oberdiek/gettitlestring.sty))
    (/usr/share/texlive/texmf-dist/tex/latex/psnfss/t1phv.fd)

    ! Package inputenc Error: Unicode char 计 (U+8BA1)
    (inputenc)                not set up for use with LaTeX.

    See the inputenc package documentation for explanation.
    Type  H <return>  for immediate help.
    ...                                              
                                                    
    l.74 \sphinxtableofcontents

解决：`pdfTex`是用于生成`pdf`文件的命令，在`Admin->Advanced Settings`中选择取消`pdf`生成选项

    Create a PDF version of your documentation with each build.

## 问题三：`/source/contents.rst not found`

更新`sphinx`版本从`v1.8.0`到`v2.2.1`，在本地编译没有问题，在`readthedocs`上发生如下问题

```
/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/recommonmark/parser.py:65: UserWarning: Container node skipped: type=document
  warn("Container node skipped: type={0}".format(mdnode.t))

Traceback (most recent call last):
  File "/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/sphinx/cmd/build.py", line 304, in build_main
    app.build(args.force_all, filenames)
  File "/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/sphinx/application.py", line 341, in build
    self.builder.build_update()
  File "/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/sphinx/builders/__init__.py", line 347, in build_update
    len(to_build))
  File "/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/sphinx/builders/__init__.py", line 360, in build
    updated_docnames = set(self.read())
  File "/home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/envs/latest/lib/python3.7/site-packages/sphinx/builders/__init__.py", line 472, in read
    self.env.doc2path(self.config.master_doc))
sphinx.errors.SphinxError: master file /home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/checkouts/latest/docs/source/contents.rst not found

Sphinx error:
master file /home/docs/checkouts/readthedocs.org/user_builds/zj-sphinx-github-readthedocs/checkouts/latest/docs/source/contents.rst not found
```

参考[Sphinx error: master file [..]/checkouts/latest/contents.rst not found #2569](https://github.com/readthedocs/readthedocs.org/issues/2569)

在`conf.py`中添加

```
master_doc = 'index'
```

原因是`readthedocs`使用的`sphinx`版本较低，导致无法找到起始页