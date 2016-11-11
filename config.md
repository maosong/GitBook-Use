# 配置

gitbook 的配置文件 book.json 非常强大，允许我们设计电子书的标题、描述、作者、语言等信息，也可以改变样式表或者为侧边栏添加链接。最为强大的是配置 gitbook 的各种使用插件，让电子书具备更强大功能。

现在我们就对上一章节的电子书增加配置文件。

```javascript
{
    "title": "我的第一本电子书",
    "author": "maosong",
    "language": "zh-hans",
    "links": {
        "sidebar": {
            "GitBook使用教程": "https://github.com/maosong/GitBook-Use"
        }
    },
    "styles": {
        "website": "styles/website.css"
    },
    "plugins": [
        "-sharing",
        "theme-api"
    ],
    "pluginsConfig": {
        "theme-api": {
            "showLevel": true
        }
    }
}
```

可以看到，我们定义了标题(title)、作者(author)、语言(language)和站外链接(links)，并附加了一个样式表文件(website.css)。插件方面，关闭了分享插件，并使用新的皮肤(theme-api)启用章节序号功能。

增加样式表 styles/website.css 文件

```css
h1, h2 {
    border-bottom: 1px solid #dcdcdc;
}
```

因为使用了新的皮肤(theme-api)，如果之前没有安装过，需要使用 gitbook 命令行安装。

```bash
$ gitbook install
```

大功告成，现在再次编译看看效果吧。
