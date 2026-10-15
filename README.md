# Software Collection

个人自用的 Windows 软件清单，每个软件附一句定位说明和可直接复制的 winget 安装命令。

> 全部命令在 **PowerShell** 中执行。批量安装可用 `winget install --id <包ID> -e`，`-e` 表示精确匹配包 ID，避免装错同名软件。

## 目录

- [系统与激活](#系统与激活)
- [系统增强](#系统增强)
- [安全防护](#安全防护)
- [网络与传输](#网络与传输)
- [开发工具](#开发工具)
- [影音与多媒体](#影音与多媒体)
- [硬件与外设](#硬件与外设)

---

## 系统与激活

### 1. MAS (Microsoft Activation Scripts)

Windows 和 Office 的激活脚本，开源、支持 HWID / Ohook 等多种方式，无需第三方破解工具。

> ⚠️ **免责声明**：本工具用于绕过 Microsoft 的授权验证。请仅在拥有合法授权的环境下用于学习研究，使用者需自行承担合规责任。

```powershell
irm https://get.activated.win | iex
```

- 官网 / 文档：https://massgrave.dev/

---

## 系统增强

### 2. NanaZip

基于 7-Zip 的现代 Windows 压缩工具，支持 Windows 11 右键菜单、暗色主题，界面比原版更贴合系统。

```powershell
winget install --id M2Team.NanaZip -e
```

- 开源仓库：https://github.com/M2Team/NanaZip

### 3. Everything

文件名秒级搜索工具，直接读 NTFS 索引，几乎不占资源。找不到文件时的第一选择。

```powershell
winget install --id voidtools.Everything -e
```

- 官网：https://www.voidtools.com/

### 4. 7-Zip

老牌开源压缩工具，格式支持全、压缩率高，命令行也常用。与 NanaZip 同源，可二选一或都装。

```powershell
winget install --id 7zip.7zip -e
```

- 官网：https://www.7-zip.org/

---

## 安全防护

### 5. 火绒安全

国产轻量杀毒软件，无弹窗广告、不捆绑，占用低。相比不少国产安全软件更适合长期常驻。

- 官网：https://www.huorong.cn/
- 说明：官方未提供 winget 包，请从官网下载安装。

---

## 网络与传输

### 6. LocalSend

跨平台局域网文件互传工具，无需联网、无需登录，手机和电脑之间直接传文件。开源且无广告。

```powershell
winget install --id LocalSend.LocalSend -e
```

- 开源仓库：https://github.com/localsend/localsend

### 7. FlClash

基于 ClashMeta 内核的多平台代理客户端，界面现代，规则配置灵活。

```powershell
winget install --id chen08209.FlClash -e
```

- 开源仓库：https://github.com/chen08209/FlClash

### 8. 网易 UU 远程

网易出品的远程控制工具，主打低延迟，对游戏场景做过优化，个人使用免费。

- 官网：https://uuyc.163.com/
- 说明：官方未提供 winget 包，请从官网下载安装。

---

## 开发工具

### 9. VS Code

主力代码编辑器，插件生态庞大，前端 / Python / 脚本开发都够用。

```powershell
winget install --id Microsoft.VisualStudioCode -e
```

- 官网：https://code.visualstudio.com/

### 10. Git

版本控制工具，开发环境必备。

```powershell
winget install --id Git.Git -e
```

- 官网：https://git-scm.com/

### 11. uv

Rust 编写的 Python 包与项目管理器，替代 pip / venv / poetry，安装依赖速度极快。

```powershell
winget install --id astral-sh.uv -e
```

- 官方文档：https://docs.astral.sh/uv/

### 12. Vite Plus

基于 Vite 的一体化前端工具链，整合开发、构建与工具集。

- 官网：https://viteplus.dev/
- 说明：官方未提供 winget 包，请从官网下载安装。

---

## 影音与多媒体

### 13. OBS Studio

开源录屏与直播推流软件，功能完整、插件丰富，免费无水印。

```powershell
winget install --id OBSProject.OBSStudio -e
```

- 官网：https://obsproject.com/

### 14. FFmpeg

音视频处理命令行工具，转码、剪辑、压制、提取音频都靠它，也是大量软件的底层依赖。

```powershell
winget install --id Gyan.FFmpeg -e
```

- 官网：https://ffmpeg.org/
- 说明：`Gyan.FFmpeg` 是 winget 上常用的 Windows 构建版本（gyan.dev）。

---

## 硬件与外设

### 15. Lenovo Legion Toolkit

联想拯救者系列的控制工具，用于调节性能模式、风扇、键盘灯效、电池充电阈值等，比官方 Vantage 轻量且无广告。

```powershell
winget install --id LenovoLegionToolkit-Team.LenovoLegionToolkit -e
```

- 开源仓库：https://github.com/LenovoLegionToolkit-Team/LenovoLegionToolkit
- 说明：仓库已从 `BartoszCichecki` 迁移至 `LenovoLegionToolkit-Team`，winget 包 ID 也同步变更，使用旧 ID 会安装失败。

---

## 批量安装（可选）

想一次性装完所有带 winget 包的软件：

```powershell
$apps = @(
  "M2Team.NanaZip",
  "voidtools.Everything",
  "7zip.7zip",
  "LocalSend.LocalSend",
  "chen08209.FlClash",
  "Microsoft.VisualStudioCode",
  "Git.Git",
  "astral-sh.uv",
  "OBSProject.OBSStudio",
  "Gyan.FFmpeg",
  "LenovoLegionToolkit-Team.LenovoLegionToolkit"
)

foreach ($app in $apps) {
  winget install --id $app -e --accept-package-agreements --accept-source-agreements
}
```

## 常用 winget 命令

| 操作 | 命令 |
| --- | --- |
| 搜索软件 | `winget search <关键字>` |
| 查看包信息 | `winget show --id <包ID> -e` |
| 安装 | `winget install --id <包ID> -e` |
| 升级全部 | `winget upgrade --all` |
| 列出已安装 | `winget list` |
| 卸载 | `winget uninstall --id <包ID> -e` |

---

## 添加新软件

在对应分类下追加一节，保持格式一致：

```markdown
### N. 软件名

一句话说明它是做什么的、以及为什么好用。

```powershell
winget install --id 包ID -e
```

- 官网：https://...
```

不确定 winget 包 ID 时，先用 `winget search <软件名>` 查出准确的 ID 和发布者，避免装到同名的第三方包。
