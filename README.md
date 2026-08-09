# 🗺️ Mapchooser Extended

[![SourceMod](https://img.shields.io/badge/SourceMod-1.10+-blue.svg)](https://www.sourcemod.net/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.11.2-orange.svg)](RELEASE_NOTES.md)

**Mapchooser Extended 分支版本，用于在 Source 引擎服务器（CS:GO、CS:S、L4D/L4D2）上管理地图选择投票**

> 📌 本项目基于 Sneaks Community 的 [sourcemod-mapchooser-extended](https://github.com/Sneaks-Community/sourcemod-mapchooser-extended)

---

## ✨ 特性

### 核心功能
- 🗳️ **地图选择投票系统** - 允许玩家为下一张地图投票
- 🎯 **地图提名** - 玩家可以提名每一张单独的地图
- 🔄 **地图轮换** - 在回合结束时自动切换
- 🎬 **Rock the Vote** - 在回合开始时可以返回当前地图

### 1.11.2 版本的改进
- ✅ 更新了聊天消息的视觉样式，使用 `[MAP]` 前缀
- ✅ 完整支持俄语（修复了翻译错误）
- ✅ 添加了 `multicolors.inc` 颜色处理库
- ✅ 从翻译文件动态加载前缀
- ✅ 扩展了对更多游戏的支持（包括 Left4Dead 1 和 2）
- ✅ 默认关闭音效（可选启用）
- 🔧 改进了游戏类型检测系统

---

## 📋 系统要求

### 游戏服务器
- **SourceMod** 1.10 及以上版本
- **支持的游戏：**
  - Counter-Strike: Global Offensive (CS:GO)
  - Counter-Strike: Source (CSS)
  - Left 4 Dead (L4D)
  - Left 4 Dead 2 (L4D2)
  - 其他基于 Source 引擎的游戏

### 从源码编译
- **SourceMod 编译器 (spcomp)** 1.10+ 版本
- SourceMod SDK 中的 include 文件

---

## 🚀 安装

### 快速安装（使用已编译插件）

1. **下载** `Mapchooser Extended 1.11.2 CSGO+CSS/` 文件夹中的文件

2. **复制到服务器目录：**
   ```
   Mapchooser Extended 1.11.2 CSGO+CSS/
   └── addons/sourcemod/    →  你的服务器/addons/sourcemod/
   └── cfg/sourcemod/       →  你的服务器/cfg/sourcemod/
   ```

3. **使用以下命令重载服务器：**
   ```
   sm_plugins reload mapchooser_extended
   ```

### 编译安装

1. **复制 include 文件：**
   ```
   addons/sourcemod/scripting/include/multicolors.inc  → 你的_include文件夹/
   addons/sourcemod/scripting/include/multicolors/      → 你的_include文件夹/
   ```

2. **编译插件：**
   ```bash
   spcomp.exe mapchooser_extended.sp -o ../plugins/mapchooser_extended.smx
   spcomp.exe nominations_extended.sp -o ../plugins/nominations_extended.smx
   spcomp.exe rockthevote_extended.sp -o ../plugins/rockthevote_extended.smx
   spcomp.exe basetriggers.sp -o ../plugins/basetriggers.smx
   ```

3. **音效（可选）：**
   - 将 `mapchooser_extended_sounds.smx` 从 `disabled` 文件夹移动到 `plugins` 文件夹

> 📖 详细说明：[INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md)

---

## 📁 文件结构

```
├── addons/sourcemod/
│   ├── configs/
│   │   └── mapchooser_extended/     # 配置文件
│   │       ├── maps/                # 按游戏分类的地图列表
│   │       └── sounds/              # 声音文件
│   ├── plugins/
│   │   ├── mapchooser_extended.smx     # 主插件
│   │   ├── nominations_extended.smx    # 提名插件
│   │   ├── rockthevote_extended.smx    # RTV 插件
│   │   ├── basetriggers.smx            # 基础触发器
│   │   └── disabled/
│   │       └── mapchooser_extended_sounds.smx  # 音效（已隔离）
│   ├── scripting/
│   │   ├── *.sp                     # 插件源文件
│   │   └── include/                 # 库文件（inc 文件）
│   └── translations/
│       └── *.phrases.txt            # 翻译文件
└── cfg/sourcemod/
    └── mapchooser_extended.cfg      # 主配置文件
```

---

## ⚙️ 配置

### 主配置文件
编辑 `cfg/sourcemod/mapchooser_extended.cfg` 进行配置：

```cfg
// 投票时长（秒）
sm_mapvote_time "15"

// 投票列表中最少的地图数量
sm_mapvote_endround_time "20"

// 显示当前得票排名
sm_mapvote_showrank "1"

// 自动更换地图所需的投票百分比
sm_mapvote_playerveto "1"
```

> 📖 完整文档：[README_DOCUMENTATION.md](README_DOCUMENTATION.md)

---

## 📊 与原版的区别

各版本的详细对比请参阅文档文件：

| 功能 | 1.11.1 | 1.11.2 |
|---------|--------|--------|
| 视觉样式 | 基础 | 带颜色的 [MAP] 前缀 |
| 俄语支持 | 部分 | 完整 ✓ |
| Multicolors | ✗ | ✓ |
| Left4Dead | ✗ | ✓ |
| 默认音效 | 启用 | 关闭 |
| 动态前缀 | ✗ | ✓ |

> 📋 详细对比：[DETAILED_COMPARISON.md](DETAILED_COMPARISON.md)

---

## 📚 文档

- **[README_DOCUMENTATION.md](README_DOCUMENTATION.md)** — 全部文档导航
- **[RELEASE_NOTES.md](RELEASE_NOTES.md)** — 1.11.2 版本更新
- **[INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md)** — 详细安装说明
- **[CHANGELOG_1.11.2_RU.md](CHANGELOG_1.11.2_RU.md)** — 完整更新日志
- **[DETAILED_COMPARISON.md](DETAILED_COMPARISON.md)** — 版本技术对比

---

## 🛠️ 开发

### 编译插件

使用 SourceMod 内置编译器并启用优化：

```bash
spcomp.exe plugin.sp -i ./include -O2 -t4 -v2
```

**参数：**
- `-i` — include 文件路径
- `-O2` — 优化级别
- `-t4` — 4 线程编译
- `-v2` — 详细输出

### 源码结构

所有 `.sp` 源文件位于 `addons/sourcemod/scripting/` 文件夹：

- `mapchooser_extended.sp` — 地图选择系统核心
- `nominations_extended.sp` — 提名系统
- `rockthevote_extended.sp` — RTV 系统
- `basetriggers.sp` — 基础系统触发器

Include 库：
- `mapchooser_extended.inc` — 主 API
- `multicolors.inc` — 彩色消息处理
- `nativevotes.inc` — 投票系统

---

## 🤝 致谢

感谢 **Sneaks Community** 的 **[sourcemod-mapchooser-extended](https://github.com/Sneaks-Community/sourcemod-mapchooser-extended)** 项目为本分支提供了出色的基础。

---

## 📝 许可证

本项目基于 **MIT** 许可证发布。详情请参阅 LICENSE 文件。

---

## 🔗 相关链接

- **Snapshots Discord 服务器：** https://discord.gg/tWGJnE3DVU
- **SourceMod 文档：** https://www.sourcemod.net/
- **原项目：** https://github.com/Sneaks-Community/sourcemod-mapchooser-extended

---

## 💬 调试与帮助

如果您遇到问题：

1. 查看 [INSTALL_GUIDE_1.11.2.md](INSTALL_GUIDE_1.11.2.md) 中的"问题排查"部分
2. 确认已复制所有 include 文件
3. 检查服务器日志：`addons/sourcemod/logs/`
4. 使用 `sm plugins list` 命令检查插件状态

---

**版本：** 1.11.2  
**最后更新：** 2026 年 3 月  
**原始版本：** Sneaks-Community/sourcemod-mapchooser-extended
