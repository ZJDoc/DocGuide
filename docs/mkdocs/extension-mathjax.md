
# [插件]MathJax

## 配置

在`mkdocs.yml`中添加

```
# markdown扩展
markdown_extensions:
  # 参考[MathJax](https://squidfunk.github.io/mkdocs-material/reference/mathjax/)，支持数学公式渲染
  - pymdownx.arithmatex:
      generic: true

# mathjax
extra_javascript:
  - javascripts/config.js
  - https://polyfill.io/v3/polyfill.min.js?features=es6
  - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
```

## 使用

```
$$
y = x + 5
$$
```

$$
y = x + 5
$$

## 相关阅读

* [MathJax](https://squidfunk.github.io/mkdocs-material/reference/mathjax/)