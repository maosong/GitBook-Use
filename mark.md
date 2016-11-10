# 制作

Node.js 和 gitbook 已经安装完毕，接下来我们来制作第一本电子书。

## 创建电子书目录

```bash
$ mkdir gitbook-first
```

## 初始化工具

我们通过gitbook命令行初始化电子书。

```bash
$ cd gitbook-first
$ gitbook init
```

可能的输出：

```
warn: no summary file in this book
info: create README.md
info: create SUMMARY.md
info: initialization is finished
```

至此，我们得到了 README.md（电子书简介）和 SUMMARY.md（电子书目录结构）这两个必备文件。

## 目录设计

接下来，要修改 SUMMARY.md 文件，构建我们的电子书目录。

```bash
$ vi SUMMARY.md
```

```markdown
# 摘要

* [简介](README.md)
* [Node.js](nodejs/README.md)
    * [NVM](nodejs/nvm.md)
    * [NPM](nodejs/npm.md)
    * [Bable](nodejs/bable.md)
* [Webpack](webpack/README.md)
    * [安装](webpack/install.md)
    * [配置](webpack/configure.md)
    * [编译项目](webpack/compile.md)
```

完成目录设计后，我们再次调用初始化工具，它会根据 SUMMARY.md 的定义，为我们创建相应的文件（夹）。

```bash
$ gitbook init
```

可能的输出：

```
info: create nodejs/README.md
info: create nodejs/nvm.md
info: create nodejs/npm.md
info: create nodejs/bable.md
info: create webpack/README.md
info: create webpack/install.md
info: create webpack/configure.md
info: create webpack/compile.md
info: create SUMMARY.md
info: initialization is finished
```

## 生成图书

### 预览服务器

我们可以通过 gitbook 的预览服务器实时预览电子书。

```bash
$ gitbook serve --port 8080
```

在浏览器中输入 http://localhost:8080 即可。

仔细一点会发现生成了 \_book 文件夹，这是 gitbook 的编译结果。

### 静态网站

我们也可以通过 gitbook 的构建工具，生成静态网站文件到 \_book 文件夹：

```bash
$ gitbook build
```

可能的输出：

```
info: 7 plugins are installed
info: 6 explicitly listed
info: loading plugin "highlight"... OK
info: loading plugin "search"... OK
info: loading plugin "lunr"... OK
info: loading plugin "sharing"... OK
info: loading plugin "fontsettings"... OK
info: loading plugin "theme-default"... OK
info: found 9 pages
info: found 0 asset files
info: >> generation finished with success in 1.0s !
```

### PDF

未完成
