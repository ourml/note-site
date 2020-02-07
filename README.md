### 记录学习、工作中的知识点

#### 什么是 Hexo?

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](https://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。[Hexo 官网](https://hexo.io/zh-cn/)

#### 安装前提
安装 Hexo 相当简单，只需要先安装下列应用程序即可：

Node.js (Node.js 版本需不低于 8.10，建议使用 Node.js 10.0 及以上版本)
Git
如果您的电脑中已经安装上述必备程序，那么恭喜您！你可以直接前往 安装 Hexo 步骤。

如果您的电脑中尚未安装所需要的程序，请根据以下安装指示完成安装。

#### 安装

* **安装 Git**

  - Windows：下载并安装 [git](https://git-scm.com/download/win).
  - Mac：使用 [Homebrew](http://mxcl.github.com/homebrew/), [MacPorts](http://www.macports.org/) 或者下载 [安装程序](http://sourceforge.net/projects/git-osx-installer/)
  - Linux (Ubuntu, Debian)：`sudo apt-get install git-core`
  - Linux (Fedora, Red Hat, CentOS)：`sudo yum install git-core`

  > **Mac 用户**
  >
  > 如果在编译时可能会遇到问题，请先到 App Store 安装 Xcode，Xcode 完成后，启动并进入 **Preferences -> Download -> Command Line Tools -> Install** 安装命令行工具。

  > **Windows 用户**
  >
  > 对于中国大陆地区用户，可以前往 [淘宝 Git for Windows 镜像](https://npm.taobao.org/mirrors/git-for-windows/) 下载 git 安装包。

*  **安装 Node.js**
  * Node.js 为大多数平台提供了官方的 [安装程序](https://nodejs.org/en/download/)。对于中国大陆地区用户，可以前往 [淘宝 Node.js 镜像](https://npm.taobao.org/mirrors/node) 下载。
  * 其它的安装方法：
    * Windows：通过 [nvs](https://github.com/jasongin/nvs/)（推荐）或者[nvm](https://github.com/nvm-sh/nvm) 安装。
    * Mac：使用 [Homebrew](https://brew.sh/) 或 [MacPorts](http://www.macports.org/) 安装。
    * Linux（DEB/RPM-based）：从 [NodeSource](https://github.com/nodesource/distributions) 安装。
    * 其它：使用相应的软件包管理器进行安装，可以参考由 Node.js 提供的 [指导](https://nodejs.org/en/download/package-manager/)

对于 Mac 和 Linux 同样建议使用 nvs 或者 nvm，以避免可能会出现的权限问题。

> **Windows 用户**
>
> 使用 Node.js 官方安装程序时，请确保勾选 **Add to PATH** 选项（默认已勾选）

> **For Mac / Linux 用户**
>
> 如果在尝试安装 Hexo 的过程中出现 `EACCES` 权限错误，请遵循 [由 npmjs 发布的指导](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) 修复该问题。强烈建议 **不要** 使用 root、sudo 等方法覆盖权限

* **安装 Hexo**

```bash
npm install -g hexo-cli hexo-server
```

#### 运行

进入到项目文件夹

```bash
# 初始化子模块
git submodule init
# 拉取子模块最新内容
git submodule update
# 安装项目依赖
npm install
# 启动服务
hexo server
```

启动服务后，在浏览器打开[http://localhost:4000](http://localhost:4000)即可看到效果

