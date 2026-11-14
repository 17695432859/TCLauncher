# TCraft Launcher

> 轻一点，快一点的《我的世界》Java 版启动器

![版本](https://img.shields.io/badge/version-1.0.0-orange)

![协议](https://img.shields.io/badge/license-MIT-green)



![平台](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blue)

![Java](https://img.shields.io/badge/Java-17%2B-red)

TCraft Launcher（简称 TCL）是一个用 **JavaFX 从头重写**的免费开源 Minecraft 启动器。单文件发布、无安装向导、无捆绑、无统计上报，拷到哪儿都能跑。

装游戏、装加载器、装整合包、开房间联机——这些流程在这里是一条线，而不是五个网页加三个文件夹来回跳。

![主界面](assets/screenshot.jpg)

---

## 特性

|    | 能力       | 说明                                                                           |
| -- | -------- | ---------------------------------------------------------------------------- |
| 🧩 | **版本管理** | 自动安装原版，以及 Fabric / Forge / NeoForge / OptiFine；Modrinth 与 CurseForge 整合包一键导入 |
| 🔑 | **正版登录** | 微软账号一键登录，浏览器里登完自动跳回，不用手动复制链接；同时支持离线模式与外置 Authlib（如 LittleSkin）               |
| 🌐 | **联机房间** | 基于 EasyTier 虚拟局域网。建个房间把邀请码发给朋友即可联机，单机存档也能开，不需要公网 IP                          |
| ⬇️ | **资源下载** | 游戏、Mod、光影、材质包一站下载；多个镜像自动测速，慢的自动切换                                            |
| 📦 | **实例隔离** | 每个实例独立的版本、存档与 Mod，互不干扰；内存与 Java 运行时可按实例单独设置                                  |
| 🎨 | **个性化**  | 主题色从你的壁纸里自动提取；另有 30 种预设色板，动画速度、组件透明度都能调                                      |

## 下载

前往 [GitHub Releases](https://github.com/DamianJiang/TCraft-Launcher/releases) 下载对应平台的安装包：

| 平台      | 文件                         | 说明                       |
| ------- | -------------------------- | ------------------------ |
| Windows | `TCraftLauncher-*-win.exe` | 双击运行，首次启动自动解压            |
| macOS   | `*-mac*.jar` / `.command`  | Intel 与 Apple Silicon 分包 |
| Linux   | `*-linux.sh` / `.deb`      | x86_64 与 aarch64         |

## 运行要求

- **Java 17 或更高版本**。启动器自带 JavaFX，但**不带 JRE**，检测不到 Java 时会给出下载指引。
- 首次运行会把资源与运行库解压到 `~/.tcraft-launcher-javafx/`。
- 联机功能首次使用会自动下载 EasyTier：Windows 需要管理员权限，macOS 按弹窗授权，Linux 建议用 `sudo` 运行。

## 从源码构建

仓库里直接带了各平台的 JavaFX 运行库，不需要额外配置依赖。JDK 17 以上，克隆下来就能编译：

```bash
# 编译
javac --module-path lib --add-modules javafx.controls,javafx.graphics,javafx.base,javafx.media \
      -encoding UTF-8 -d out src/tcraft/*.java

# 运行
java --module-path lib --add-modules javafx.controls,javafx.graphics,javafx.base,javafx.media \
     -cp out tcraft.Boot
```

仓库结构：

```
src/tcraft/    源码
res/           图标、语言表、样式
lib/           JavaFX 运行库
tools/         原生启动器（launcher.c）
website/       官网
```

## 上手三步

1. **登录** —— 顶部账号区点一下，选微软正版登录或离线模式。
2. **建实例** —— 「实例」页新建，选游戏版本与加载器，需要的话顺手导入整合包。
3. **开玩** —— 回首页点启动。要联机就去「联机」页建房间，把邀请码发给朋友。

## 已知问题

v1.0.0 是一次彻底重写的产物，架构和界面都是新的——干净，但还没磨完：

- 部分功能仍在打磨，**个别设置项可能不生效**；
- **macOS 与 Linux 尚未经过充分测试**，遇到问题更适合提 Issue，而不是指望立刻修好；
- 联机首次使用需要下载 EasyTier，且涉及权限（见上文）。

如果只是想稳定日常使用，HMCL、PCL2 目前仍然更稳妥。这个项目更适合愿意尝鲜、愿意反馈问题的人。

## 常见问题

**Q：这个 TCL 和 TCL 电视、TCL 品牌有关系吗？**  
没有。这里的 TCL 是 **T**Craft **L**auncher 的缩写。

**Q：需要自己装 Java 吗？**  
需要 Java 17+。单文件版检测不到时会给出下载指引，装完再启动即可。

**Q：为什么启动器这么大？**  
因为里面打包了各平台的 JavaFX 运行库，换来的是「解压即用、不用配环境」。

**Q：支持正版和离线两种模式吗？**  
都支持。正版走微软账号 OAuth，离线模式可以自定义用户名，也能接外置 Authlib 皮肤站。

## 反馈与贡献

- 遇到 Bug 或有功能建议：请到 [Issues](https://github.com/DamianJiang/TCraft-Launcher/issues) 提交，附上系统版本、Java 版本和日志。
- 提交代码：欢迎 Fork 后发起 Pull Request，尽量一个 PR 只做一件事。
- 交流群：QQ 1131373915

## 开源协议

本项目基于 [MIT License](LICENSE) 开源。你可以自由使用、修改、分发，包括商业用途，请保留原作者的版权声明。

Minecraft 是 Mojang Studios 的商标，本项目与 Mojang 及 Microsoft 无隶属关系。

## 致谢

- [JavaFX](https://openjfx.io/) —— 界面框架
- [EasyTier](https://github.com/EasyTier/EasyTier) —— 联机虚拟局域网
- [Modrinth](https://modrinth.com/) / [CurseForge](https://www.curseforge.com/) —— 整合包与资源来源
- 以及所有提过 Issue、测过版本的玩家

---

官网：<https://damianjiang.github.io/TCraft-Launcher/> · 仓库：<https://github.com/DamianJiang/TCraft-Launcher>
