
# Markdown配置

`sphinx`支持`markdown`，使用的是[CommonMark](https://commonmark.org/)语法

## 配置

需要安装`recommonmark`

```
$ pip install --upgrade recommonmark
```

然后在配置文件`conf.py`中添加`Markdown`解析器

```
# Add any Sphinx extension module names here, as strings. They can be
# extensions coming with Sphinx (named 'sphinx.ext.*') or your custom
# ones.
extensions = ['recommonmark']
```

增加`'.md'`作为扩展名

```
source_suffix = {
    '.rst': 'restructuredtext',
    '.txt': 'markdown',
    '.md': 'markdown',
}
```

## 相关阅读

* [Markdown](https://www.sphinx-doc.org/en/master/usage/markdown.html#markdown)