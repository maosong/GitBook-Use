# 命令

首先说明，gitbook-cli 和 gitbook 是两个软件，gitbook-cli 将 gitbook 的不同版本下载到 ~/.gitbook中，可以通过设置GITBOOK\_DIR 环境变量来指定另外的文件夹。

这里我们列出 gitbook 常用命令行 。

**列出gitbook所有的命令**

```bash
$ gitbook help
```

**输出gitbook-cli的帮助信息**

```bash
$ gitbook --help
```

初始化电子书

```bash
$ gitbook init
```

**生成静态网页**

```bash
$ gitbook build
```

**生成静态网页并运行服务器**

```bash
$ gitbook serve
```

**生成时指定gitbook的版本, 本地没有会先下载**

```bash
$ gitbook build --gitbook=2.0.1
```

**列出本地所有的gitbook版本**

```bash
$ gitbook ls
```

**列出远程可用的gitbook版本**

```bash
$ gitbook ls-remote
```

**安装对应的gitbook版本**

```bash
$ gitbook fetch 标签/版本号
```

**更新到gitbook的最新版本**

```bash
$ gitbook update
```

**卸载对应的gitbook版本**

```bash
$ gitbook uninstall 2.0.1
```

**指定log的级别**

```bash
$ gitbook build --log=debug
```

**输出错误信息**

```bash
$ gitbook builid --debug
```
