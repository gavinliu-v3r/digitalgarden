---
{"aliases":["yazi","文件管理器","terminal-file-manager"],"created":"Saturday, April 4th 2026, 1:57:27 pm","modified":"Saturday, April 4th 2026, 2:01:08 pm","dg-publish":true,"tags":["domain/software","domain/linux"],"related":"","author":"Gavin","permalink":"/03-Software & Tools/yazi - 现代终端文件管理器/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":["yazi","文件管理器","terminal-file-manager"],"created":"Saturday, April 4th 2026, 1:57:27 pm","modified":"Saturday, April 4th 2026, 2:01:08 pm","tags":["domain/software","domain/linux"],"related":"","author":"Gavin"}}
---


## 快速开始

### 安装

```bash
# macOS
brew install yazi

# Linux (Arch)
sudo pacman -S yazi

# 依赖安装
# macOS
brew install ripgrep fd fzf bat eza

# Linux
sudo pacman -S ripgrep fd fzf bat eza
```

### 启动

```bash
yazi          # 在当前目录启动
yazi /path    # 指定目录启动
yazi --chooser # 选择模式
```

## 核心快捷键

### 文件浏览

- `h/←` - 返回上级
- `l/→` - 进入目录
- `gg` - 跳到顶部
- `G` - 跳到底部
- `/` - 搜索文件
- `f` - 文件名筛选

### 文件操作

- `yy` - 复制文件名
- `ya` - 复制完整路径
- `dd` - 剪切
- `pp` - 粘贴
- `ww` - 重命名
- `zn` - 新建文件
- `zd` - 新建目录
- `dd` - 删除

### 视图控制

- `w` - 切换侧边栏
- `i` - 显示隐藏文件
- `1-5` - 切换布局
- `q` - 退出

## 实用技巧

### 批量选择

- `Space` - 选择/取消选择
- `V` - 反向选择
- `Ctrl+a` - 全选
- `Ctrl+r` - 反选

### 快速预览

- `l` / `Enter` - 进入文件
- `Backspace` - 返回
- `Tab` - 切换预览

### 工作流

```bash
# 在 vim 中打开选中文件
yazi --chooser | xargs nvim

# 在当前目录打开 yazi
cd /path/to/project && yazi

# 快速创建项目结构
yazi /tmp && # 创建完文件后复制到目标目录
```

## 配置个性化

### 添加自定义快捷键

```toml
# ~/.config/yazi/yazi.toml
[manager]
keys = [
  { on = [ "o" ], run = "open", desc = "Open with default app" },
  { on = [ "g" ], run = "cd ~", desc = "Go to home" },
]
```

### 自定义主题

```toml
# ~/.config/yazi/theme.toml
[manager]
cwd = { fg = "blue" }
selected = { fg = "yellow" }
```
