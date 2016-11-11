# 皮肤

GitBook默认皮肤非常棒，也有一定程度的自定义功能，而且[插件库](http://plugins.gitbook.com)也有一些优秀皮肤（比如官方制作的API样式），但远不能满足各种个性化需求，现在我们就来看看如何建立新的GitBook皮肤。

根据[官方介绍](https://toolchain.gitbook.com/themes/)，皮肤属于GitBook的插件，需要在[npmjs](https://www.npmjs.com)发布，包命名应该以 gitbook-plugin-theme 为前缀，使用[Nunjucks模板语言](https://mozilla.github.io/nunjucks/)编写。皮肤需要的上下文引用、变量可以参考[官方文档](https://toolchain.gitbook.com/templating/)。

本着快速开始的原则（学习文档重新构建花时间较多），我们以官方的 [theme-default](https://github.com/GitbookIO/theme-default) 为基础修改建立新皮肤。

## 下载 theme-default

使用 git 命令行下载 theme-default 的最新版本。

```bash
$ git clone -b 1.0.6 https://github.com/GitbookIO/theme-default.git
```

## 安装依赖

```bash
$ cd theme-maosong
$ npm install
```

## 修改相关文件

首先，我们将 theme-default 改名为 theme-maosong（请把 maosong 替换为你的模板名称）。

```bash
$ mv theme-default theme-maosong
```

**package.json**

修改如下参数：

```javascript
{
    "name": "gitbook-plugin-theme-maosong",
    "description": "Theme for GitBook",
    "version": "1.0.0",
    "repository": {
        "type": "git",
        "url": "https://github.com/maosong/theme-maosong.git"
    },
    "author": "maosong <maosong@ioophp.com>",
    "license": "Apache-2.0",
    "bugs": {
      "url": "https://github.com/maosong/theme-maosong/issues"
    },
    "contributors": [
      {
        "name": "maosong",
        "email": "maosong@ioophp.com"
      }
    ]
}
```

其中 repository 和 bugs 不是必须的。

**index.js**

找到 theme-default 改为 theme-maosong。

**README.md**

说明文件。

**_layouts/website/summary.html**

现在我们对侧边栏做一些简单调整，删除 GitBook 链接，并且将 links 移到目录下方。

找到 `<ul class="summary">` 标签，替换为以下内容：

```html
<ul class="summary">
    {% for part in summary.parts %}
        {% if part.title %}
        <li class="header">{{ part.title }}</li>
        {% elif not loop.first %}
        <li class="divider"></li>
        {% endif %}
        {{ articles(part.articles, file, config) }}
    {% endfor %}

    {% if config.links.sidebar  %}
    <li class="divider"></li>
        {% for linkTitle, link in config.links.sidebar  %}
        <li>
            <a href="{{ link }}" target="_blank" class="custom-link">{{ linkTitle }}</a>
        </li>
        {% endfor %}
    {% endif %}
</ul>
```

## 发布到npm

首先，我们需要有一个npmjs账号，[点此注册](https://www.npmjs.com/signup)，然后使用npm命令行登录。

⚠️ 注意！如果使用淘宝镜像，请切换回官方镜像，否则无法发布！

```bash
$ npm login
Username: ***
Password: ***
Email: (this IS public) ***
```

现在可以使用命令行发布了。

```bash
$ npm publish
```

## 在项目中使用

回到我们的 gitbook-first 项目，修改 book.json 文件增加新模板。

```javascript
{
    "plugins": [
        "theme-maosong"
    ]
}
```

使用 gitbook 安装新模板，然后重新编译看看效果吧。

```bash
$ gitbook install
$ gitbook build
```
