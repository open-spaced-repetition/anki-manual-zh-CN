# 自托管同步服务器

> 原文：[Sync Server - Anki Manual (ankiweb.net)](https://docs.ankiweb.net/sync-server.html)

不愿意或无法使用 AnkiWeb 的高级用户可以选择使用自托管同步服务器。

需要注意的事项：

- 这是一个高级功能，适用于熟悉网络和命令行的用户。如果使用此功能，你需自行解决遇到的任何设置、网络、
  或防火墙问题，使用风险需自行承担。
- 较新的客户端可能依赖于同步协议的更改，因此如果你更新 Anki 客户端而没有同时更新服务器，可能会导致同
  步停止工作。
- 也存在第三方同步服务器。没有进行针对它们的测试，并且当同步协议更改时，第三方服务器通常需要时间来追
  赶，因此不推荐使用。
- Anki 内部消息仍会使用「AnkiWeb」这一术语，即使已配置自定义服务器（例如，当服务器宕机时显示「无法连
  接到 AnkiWeb」）。

## 安装/运行

有多种方式可以安装和运行服务器。你可以选择以下方式：

- 使用捆绑在 Anki 桌面版本中的同步服务器
- 独立的最小同步服务器，不包含 Anki 的 GUI 依赖项。提供 Python 和 Rust 实现。

### 从打包好构建开始

这是使用 Anki 桌面版本 2.1.57+ 中内建的同步服务器。

在 Windows 的 cmd.exe 中：

```bash
set SYNC_USER1=user:pass
"\Program Files\anki\anki.exe" --syncserver
```

在 MacOS 的 Terminal.app 中：

```bash
SYNC_USER1=user:pass /Applications/Anki.app/Contents/MacOS/anki --syncserver
```

在 Linux 中：

```bash
SYNC_USER1=user:pass anki --syncserver
```

### 使用 Pip

为了避免下载桌面 Anki 的 GUI 依赖项，你可以通过 PyPI 下载的 Python 包运行独立的 Anki 同步服务器。确
保你已安装 Python 3.9+。

```bash
python3 -m venv ~/syncserver
~/syncserver/bin/pip install anki
SYNC_USER1=user:pass ~/syncserver/bin/python -m anki.syncserver
```

### 使用 Cargo

从 Anki 2.1.66+ 开始，你可以使用以下命令构建 Rust 实现的独立同步服务器。确保已安装 Rustup。

```bash
cargo install --git https://github.com/ankitects/anki.git --tag 2.1.66 anki-sync-server
```

用最新的 Anki 版本替换 2.1.66。

需要安装 Protobuf（protoc）。

构建后，你可以通过以下命令运行：

```bash
SYNC_USER1=user:pass anki-sync-server
```

### 从源码检出

如果你从 GitHub 克隆了 Anki 仓库，可以从源代码安装：

```bash
./ninja extract:protoc
cargo install --path rslib/sync
```

## 多用户

`SYNC_USER1` 声明第一个用户和密码，必须设置。如果希望设置多个账户，可以选择性地声明
`SYNC_USER2`、`SYNC_USER3` 等。

## 哈希密码

高级用户可能希望使用哈希密码而不是明文密码。如果你希望这样做，需要使用单独的工具（例
如[这个](https://git.sr.ht/~laalsaas/pbkdf2-password-hash)）生成密码哈希。然后可以通过设置环境变量
PASSWORDS_HASHED 为 1（或其他任意值）来告知服务器期望使用哈希密码。

使用哈希密码时，SYNC_USER 变量应采用 username:password_hash 格式，其中 password_hash 是密码的 PHC 格
式哈希。

## 存储位置

服务器需要在文件夹中存储一份你的集合和媒体的副本。默认情况下是在 ~/.syncserver；你可以通过定义
`SYNC_BASE` 环境变量来更改此位置。这不应与正常的 Anki 数据文件夹相同，因为服务器和客户端必须分别存储
副本。

## 公开访问

服务器监听未加密的 HTTP 连接，因此不建议直接将其暴露在互联网上。 你需要将使用限制在本地网络，或在服
务器前面使用某种加密形式，例如 VPN（Tailscale 显然很简单）或 HTTPS 反向代理。

你可以定义 `SYNC_HOST` 和 `SYNC_PORT` 来更改服务器绑定的主机和端口。

## 客户端设置

你需要确定计算机的网络 IP 地址，然后将每个 Anki 客户端指向该地址，例如
`http://192.168.1.200:8080/`。 可以在首选项中配置此 URL。

如果你使用 AnkiMobile 且无法连接到本地网络上的服务器，请进入 iOS 设置，找到 Anki 并关闭再打开「允许
Anki 访问本地网络」选项。

旧版桌面客户端需要你定义 `SYNC_ENDPOINT` 和 `SYNC_ENDPOINT_MEDIA`。如果使用旧版客户端，你需将其设置
为例如 `http://192.168.1.200:8080/sync/` 和 `http://192.168.1.200:8080/msync/`。AnkiDroid 2.16 之前
的客户端需要为这两个端点单独配置。

## 反向代理

如果使用反向代理提供 HTTPS 访问（例如 nginx），并绑定到子路径（例如 `http://example.com/custom/` ->
`http://localhost:8080/`），你必须在配置 Anki 时确保使用斜杠结尾。如果你设置为
`http://example.com/custom`，将无法正常工作。

在 iOS 上，不支持 TLS 1.3，因此你的反向代理需启用 TLS 1.2，否则会出现「错误码 -9836」。

## 大型请求

默认应用了 AnkiWeb 在上传上的标准限制。 如果你希望增加限制，可选择设置 `MAX_SYNC_PAYLOAD_MEGS` 为大
于 100 的值。 请记住，如果你使用反向代理，也可能需要在那里调整限制。

## 贡献更改

由于此服务器与 Anki 一同捆绑，简洁是设计目标——其目标是面向个人/家庭使用，PR 中增加 REST API 或外部数
据库等内容的请求在当前阶段可能不被接受。如有疑问，请在开始 PR 工作之前联系我们。

如果你正在寻找现有的 API 解决方案，AnkiConnect 插件或许能满足你的需求。
