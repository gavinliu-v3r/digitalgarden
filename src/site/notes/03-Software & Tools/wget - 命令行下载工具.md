---
{"aliases":["wget","download-tool","command-line-downloader"],"created":"Saturday, April 4th 2026, 2:09:22 pm","modified":"Saturday, April 4th 2026, 2:13:05 pm","dg-publish":true,"tags":["domain/software","domain/linux"],"related":["200_Areas/200_实用指南/208_Software/kitty.md","200_Areas/200_实用指南/208_Software/IDEA.md"],"author":"Gavin","permalink":"/03-Software & Tools/wget - 命令行下载工具/","dgPassFrontmatter":true,"dg-note-properties":{"aliases":["wget","download-tool","command-line-downloader"],"created":"Saturday, April 4th 2026, 2:09:22 pm","modified":"Saturday, April 4th 2026, 2:13:05 pm","tags":["domain/software","domain/linux"],"related":["200_Areas/200_实用指南/208_Software/kitty.md","200_Areas/200_实用指南/208_Software/IDEA.md"],"author":"Gavin"}}
---


## 安装

### macOS

```bash
# M1/M2 芯片
brew install wget

# 或使用源码安装
curl -O https://ftp.gnu.org/gnu/wget/wget-latest.tar.gz
tar -xzf wget-latest.tar.gz
cd wget-*
./configure
make
sudo make install
```

### Linux

```bash
# Ubuntu/Debian
sudo apt install wget

# Arch Linux
sudo pacman -S wget

# CentOS/RHEL
sudo yum install wget
```

### Windows

```bash
# 使用 Chocolatey
choco install wget

# 或从官网下载
# https://eternallybored.org/misc/wget/
```

## 基本用法

### 简单下载

```bash
# 下载单个文件
wget https://example.com/file.zip

# 下载并重命名
wget -O newname.zip https://example.com/file.zip

# 后台下载
wget -b https://example.com/large-file.iso
```

### 断点续传

```bash
# 断点续传
wget -c https://example.com/large-file.zip

# 限制速度下载（50KB/s）
wget --limit-rate=50k https://example.com/file.zip
```

### 批量下载

```bash
# 下载整个网站（镜像）
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.com

# 下载多个文件
wget -i urls.txt

# 递归下载（深度为2）
wget -r -l 2 http://example.com
```

## 高级选项

### 文件过滤

```bash
# 只下载特定扩展名
wget --accept=pdf,jpg http://example.com/files/

# 排除特定文件
wget -R "*.jpg,*.gif" http://example.com

# 下载图片
wget -r -l 1 -A "jpg,jpeg,png,gif" http://example.com/images/
```

### 用户认证

```bash
# HTTP 基本认证
wget --http-user=username --http-password=password http://example.com/protected/

# 使用 cookies
wget --cookies=on --keep-session-cookies http://example.com/

# 代理认证
wget --proxy-user=user --proxy-pass=pass http://example.com/
```

### 重试和超时

```bash
# 设置超时（秒）
wget --timeout=30 https://example.com/

# 重试次数
wget --tries=5 https://example.com/

# 延迟下载
wget --wait=5 --limit-rate=100k https://example.com/
```

## 实用技巧

### 配置文件

```bash
# 创建配置文件
nano ~/.wgetrc

# 添加常用配置
user_agent = "Mozilla/5.0 (compatible; wget)"
accept = html,text
retry-connrefused = on
waitretry = 10
```

### 监控下载进度

```bash
# 实时查看下载进度
tail -f wget-log

# 使用 progress-bar
wget --progress=dot:mega https://example.com/large-file.zip
```

### 配合脚本使用

```bash
#!/bin/bash
# 批量下载脚本
for url in $(cat urls.txt); do
    wget --continue --timeout=30 --tries=3 $url
done
```

### 与其他工具组合

```bash
# 使用 aria2c 加速
wget -c https://example.com/file.zip && aria2c -x 16 -s 16 file.zip

# 下载并解压
wget -O - https://example.com/archive.tar.gz | tar -xzf -

# 下载并校验
wget https://example.com/file.sha256
wget https://example.com/file.zip
sha256sum -c file.sha256
```

## 常用参数速查

| 参数 | 说明 |
|------|------|
| `-c` | 断点续传 |
| `-r` | 递归下载 |
| `-n` | 递归但不创建目录 |
| `-k` | 转换链接为本地 |
| `-p` | 下载所有资源 |
| `-A` | 接受的扩展名 |
| `-R` | 排除的文件 |
| `-I` | 包含的目录 |
| `-X` | 排除的目录 |
| `-l` | 递归深度 |
| `-m` | 镜像模式 |

---

*wget - 让下载更简单高效*
