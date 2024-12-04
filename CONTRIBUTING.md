# 参与 Anki 手册的编写

## 本地开发环境搭建

Anki 手册采用 [mdBook](https://rust-lang.github.io/mdBook/)构建，这是一个基于Rust的工具，用于将Markdown文件转换成网页。

### 安装必要的软件

在使用mdBook之前，请确保你的计算机上已安装 [Rust](https://www.rust-lang.org/tools/install)。

然后，通过以下命令安装 mdBook 及其相关的预处理器：
```
cargo install mdbook
cargo install mdbook-toc
cargo install mdbook-linkcheck
```

### 开发和实时预览

要在本地运行 Anki 手册，首先使用以下命令构建项目：

```
mdbook build
```

接着，使用以下命令启动本地服务器并打开预览页面：

```
mdbook serve --open
```

现在，你可以编辑 `src/` 目录下的 markdown（*.md）文件，你所做的更改将实时反映在本地预览中。