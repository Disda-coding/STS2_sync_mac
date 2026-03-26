# STS2 Sync Tool (macOS Version)

这是一个专为 macOS 用户设计的脚本，用于在 **Steam 版《杀戮尖塔 2》(Slay the Spire 2)** 与 **Android 手机版** 之间同步游戏存档。

感谢scp3500作者的开源。该脚本通过Gemini翻译win版本bat脚本实现mac和安卓手机的同步
https://github.com/scp3500/STS2_Sync

## 🌟 功能特点

- **双向同步**：支持 PC 到手机、手机到 PC。
- **自动备份**：每次同步前自动备份旧存档，防止数据丢失（默认保留最近 10 次）。
- **版本适配**：自动处理 `platform_type`（Steam/None）和 `build_id` 差异。
- **云存档兼容**：同步本地存档的同时，自动更新 Steam 云存档缓存目录。

------

## 🛠️ 环境准备

在运行脚本之前，请确保你的 Mac 已经安装了 `adb` 工具。

### 1. 安装 ADB (Android Debug Bridge)

推荐使用 [Homebrew](https://brew.sh/) 安装：

Bash

```
# 如果没安装 Homebrew 请先安装，已安装请跳过
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 安装 Android 平台工具
brew install --cask android-platform-tools
```

安装完成后，在终端输入 `adb version` 确认输出正常。

### 2. 手机端准备

1. 开启 **开发者模式**（连续点击版本号 7 次）。
2. 开启 **USB 调试**。
3. **重要（小米/红米用户）**：必须开启开发者选项中的 **「禁用权限监控」**，否则脚本无法通过 `run-as` 命令读取游戏存档。

------

## 🚀 安装与使用

### 1. 下载脚本

将 `sts2_sync.sh` 下载到你希望存放备份的文件夹中。

### 2. 授予执行权限

macOS 默认不允许运行外部 shell 脚本，你需要手动赋予执行权限。打开终端，进入脚本所在目录：

Bash

```
chmod +x sts2_sync.sh
```

### 3. 运行脚本

使用数据线连接手机，然后在终端输入：

Bash

```
./sts2_sync.sh
```

------

## 📂 存档路径说明

脚本会自动识别以下 macOS 默认路径：

- **本地存档**：`~/Library/Application Support/SlayTheSpire2/steam/`
- **云存档**：`~/Library/Application Support/Steam/userdata/<SteamID>/2868840/remote/`

------

## ⚠️ 注意事项

- **首次连接**：手机会弹出“允许 USB 调试吗？”的授权框，请务必勾选“始终允许”并点击确定。
- **游戏状态**：同步前脚本会自动尝试强制停止手机端的游戏，以确保数据写入安全。
- **M1/M2/M3 兼容性**：脚本完全兼容 Apple Silicon 芯片，但在首次运行时，如果提示“无法验证开发者”，请前往 **系统设置 -> 隐私与安全性** 点击“仍要打开”。

------

## 📜 免责声明

本脚本仅供学习交流使用。虽然脚本内置了自动备份机制，但在进行大规模同步前，仍建议手动备份您的重要存档文件。作者不对因使用本脚本造成的任何数据丢失负责。
