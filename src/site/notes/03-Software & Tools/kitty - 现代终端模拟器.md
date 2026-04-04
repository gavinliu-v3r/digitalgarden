---
{"aliases":["kitty","terminal-emulator","mac-terminal"],"created":"Saturday, April 4th 2026, 2:02:22 pm","modified":"Saturday, April 4th 2026, 2:02:58 pm","dg-publish":true,"tags":["domain/software"],"related":["200_Areas/200_实用指南/208_Software/IDEA.md","000_Obsidian/000_Inbox/yazi.md"],"author":"Gavin","permalink":"/03-Software & Tools/kitty - 现代终端模拟器/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":["kitty","terminal-emulator","mac-terminal"],"created":"Saturday, April 4th 2026, 2:02:22 pm","modified":"Saturday, April 4th 2026, 2:02:58 pm","tags":["domain/software"],"related":["200_Areas/200_实用指南/208_Software/IDEA.md","000_Obsidian/000_Inbox/yazi.md"],"author":"Gavin"}}
---


## 快速开始

### macOS 安装

```bash
# 官方方式安装
curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin

# 使用 Homebrew 安装
brew install --cask kitty
```

### Linux 安装

```bash
# Arch Linux
sudo pacman -S kitty

# Ubuntu/Debian
sudo apt install kitty
```

## 核心特性

### 性能优势

- **GPU 加速**：使用 OpenGL 渲染，流畅滚动
- **轻量快速**：启动速度快，内存占用少
- **多协议支持**：支持 SSH、Telnet、Serial 等

### 现代功能

- **真彩色**：支持 24 位颜色
- **图片预览**：直接在终端显示图片
- **Unicode 支持**：完整 Emoji 和特殊字符
- **分屏功能**：轻松分割窗口

## 常用快捷键

### 窗口操作

- `Ctrl + Shift + Enter` - 垂直分屏
- `Ctrl + D` - 水平分屏
- `Ctrl + Shift + W` - 关闭当前窗口
- `Ctrl + Shift + F` - 全屏切换

### 标签页

- `Ctrl + Shift + T` - 新建标签
- `Ctrl + Shift + Q` - 关闭标签
- `Ctrl + Tab` - 下一个标签
- `Ctrl + Shift + Tab` - 上一个标签

### 光标移动

- `Ctrl + a` - 行首
- `Ctrl + e` - 行尾
- `Ctrl + u` - 删除到行首
- `Ctrl + k` - 删除到行尾

## 配置文件

### 基础配置

```bash
# 编辑配置文件
kitty +kitten edit config

# 或直接编辑
~/.config/kitty/kitty.conf
```

### 常用配置项

```conf
# 字体设置
font_size 14
font_family "JetBrains Mono"

# 颜色主题
include current-theme.conf

# 窗口大小
initial_window_width 120c
initial_window_height 30c

# 滚动
scrollback_lines 10000
```

### 主题安装

```bash
# 克隆主题
git clone https://github.com/dexpota/kitty-themes.git

# 应用主题
kitty +kitten themes --choose
```

## 实用技巧

### 快速跳转

```bash
# 使用 copilot 自动补全
kitty +kitten copilot

# 文件管理器集成
kitty +kitten file_manager
```

### SSH 连接

```conf
# 配置文件中添加
ssh_config ~/.ssh/config

# 快速连接
kitty +kitten ssh user@host
```

### 与其他工具配合

```bash
# 使用 yazi 作为文件管理器
kitty --execute "yazi"

# 与 neovim 集成
kitty +kitten ssh remote_host "cd /path && nvim"
```

## 性能优化

### GPU 配置

```conf
# 启用硬件加速
enabled_layouts tall,grid
cursor_shape beam
```

### 内存管理

```conf
# 限制历史记录
scrollback_lines 5000
strip_trailing_spaces yes
```