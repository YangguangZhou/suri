# Suri

Suri 是一个可轻松部署为静态站点的链接缩短器。不需要服务器端托管、无服务器云功能或数据库。Suri 可以在 60 秒内免费部署到 Vercel、Netlify 等平台。

Suri 对 "技术上更优越" 的 `3xx` 服务器重定向不感兴趣。Suri 只是希望你能利用你每年花 $39 购买但从未使用过的域名。

试试我的一个短链接：https://jstayton.com/tw 👉🏻 https://twitter.com/kidjustino

## 入门指南

### 一键安装（免费）

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https%3A%2F%2Fgithub.com%2Fjstayton%2Fsuri&project-name=suri&repository-name=suri)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https%3A%2F%2Fgithub.com%2Fjstayton%2Fsuri)
[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https%3A%2F%2Fgithub.com%2Fjstayton%2Fsuri)

[![Deploy to DO](https://www.deploytodo.com/do-btn-blue.svg)](https://cloud.digitalocean.com/apps/new?repo=https%3A%2F%2Fgithub.com%2Fjstayton%2Fsuri%2Ftree%2Fmaster)
[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https%3A%2F%2Fgithub.com%2Fjstayton%2Fsuri)

完成后，尝试访问你的 URL 的根路径——如果一切正常，它应该重定向回[我的 GitHub 个人资料](https://github.com/jstayton)。

### 管理链接

链接通过 [`src/links.json`](src/links.json) 管理，里面有一些初始示例：

```json
{
  "/": "https://github.com/jstayton",
  "1": "https://fee.org/articles/the-use-of-knowledge-in-society/",
  "tw": "https://twitter.com/kidjustino"
}
```

再简单不过了：键是被重定向的 "短链接" 路径，值是目标 URL。键可以是任意长度，使用任意字符的组合。`/` 是一个特殊条目，用于重定向根路径。

进行编辑，然后提交并推送到你的存储库。你选择的托管提供商应该会自动构建和部署你的更改。就这么简单！

_提示_：书签页面直接在
[GitHub 中编辑 `src/links.json`](https://github.com/jstayton/suri/edit/master/src/links.json)
（或其他位置），并使用默认的提交信息。现在告诉我，有哪个链接缩短器比这个更简单！

### 配置

环境变量用于设置配置选项。目前只有一个：

| 变量       | 描述                                                         | 值      | 默认值 |
| ---------- | ------------------------------------------------------------ | ------- | ------ |
| `SURI_JS`  | 是否使用 JavaScript 重定向而不是 `<meta>` 刷新。            | `1`, `0` | `0`    |

### 手动安装

在其他地方安装 Suri，或仅在你自己的机器上：

1. Fork 这个存储库以创建你自己的副本并克隆到你的机器。

1. 确保你有兼容版本的 [Node.js](https://nodejs.org/)（参见 [`package.json`](package.json) 中的 `engines.node`）。
   [nvm](https://github.com/nvm-sh/nvm) 是在你自己的机器上推荐的安装方法：

   ```bash
   $ nvm install
   ```

1. 使用 npm 安装依赖项：

   ```bash
   $ npm install
   ```

1. 构建静态站点：

   ```bash
   $ npm run build
   ```

1. 将生成的 `_site` 目录部署到最终目的地。

## 开发

以下是一些关于在 Suri 上进行开发的说明。有关 11ty 的详细信息——支持 Suri 的静态站点生成器——请参阅其[文档](https://www.11ty.dev/docs/)。

### 安装

按照上面的“手动安装”部分在你自己的机器上进行设置。

### 启动

启动开发服务器：

```bash
$ npm run dev
```

### 代码风格

[Prettier](https://prettier.com/) 已设置为强制执行一致的代码风格。强烈推荐
[为你的编辑器添加集成](https://prettier.io/docs/en/editors.html)，以便在保存时自动格式化。

通过命令行运行：

```bash
$ npm run lint
```

## 发布

开发完成后在 `development` 分支中，并准备好发布时，应将其合并到 `master` 分支，在那里最新的发布代码存在。[Release It!](https://github.com/release-it/release-it) 然后用于交互式地协调发布过程：

```bash
$ npm run release
```

![piratepx](https://app.piratepx.com/ship?p=e91ddd1b-31ad-4c36-b03e-be4a1e9a7678&i=suri)
