
# [插件]Emoji

## 配置

在`mkdocs.yml`中添加

```
# markdown扩展
markdown_extensions:
    # 参考[Icons + Emojis](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/)，执行Markdown Emoji
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg
```

## 使用

可以从[zhouie/markdown-emoji](https://github.com/zhouie/markdown-emoji)中查找相应的符号

:yum: :astonished: :+1:

## 相关阅读

* [Icons + Emojis](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/)