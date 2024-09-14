---
layout: blog
title: git常用命令
date: 2024-09-14 09:29:45
tags:
- git
categories:
- git
---

# 常用 Git 命令及示例

## git init
**作用**: 初始化一个新的 Git 仓库
**用法**:
```bash
git init
```
**示例**
```bash
cd my_project
git init
```
这将在当前目录中创建一个新的 Git 仓库

## git clone
**作用**: 从远程仓库克隆代码到本地
**用法**
```bash
git clone <repository-url>
```
**示例**
```bash
git clone https://github.com/user/repo.git
```
这会将远程仓库的内容复制到本地

## git status
**作用**: 查看工作目录的状态，包括哪些文件已更改、哪些文件未被跟踪等
**用法**
```bash
git status
```
运行后会显示当前工作目录的状态

## git add
**作用**: 将文件添加到暂存区（stage），准备提交
**用法**
```bash
git add
```
可以添加单个文件或用 . 添加所有更改的文件

## git commit
**作用**: 将暂存区的更改提交到本地仓库
**用法**
```bash
git commit -m "<commit-message>"
```
**示例**
```bash
git commit -m "Add new feature"
```
使用 `-m` 标志指定提交消息

## git push
**作用**: 将本地仓库的提交推送到远程仓库
**用法**
```bash
git push <remote> <branch>
```
**示例**
```bash
git push origin main
```
将本地的 `main` 分支推送到远程仓库 `origin`

## git pull
**作用**: 从远程仓库拉取最新的更改并合并到当前分支
**用法**
```bash
git pull <remote> <branch>
```
**示例**
```bash
git pull origin main
```
拉取远程仓库 `origin` 的 `main` 分支到本地，不加参数默认拉取本地分支对应的仓库分支

## git branch
**作用**: 查看、创建或删除分支
**用法**
```bash
git branch
git branch <branch-name>
git branch -d <branch-name>
```
**示例**
```bash
git branch           # 查看所有分支
git branch feature   # 创建名为 feature 的新分支
git branch -d feature  # 删除名为 feature 的分支
```

## git checkout
**作用**: 切换分支或恢复文件
**用法**
```bash
git checkout <branch-name>
git checkout -- <file>
```
**示例**
```bash
git checkout main    # 切换到 main 分支
git checkout -- index.html   # 恢复文件的更改
```

## git merge
**作用**: 合并两个分支的更改
**用法**
```bash
git merge <branch-name>
```
**示例**
```bash
git merge feature    # 将 feature 分支的更改合并到当前分支
```

## git reset
**作用**: 重置当前分支到某个特定提交，可以修改暂存区和工作区
**用法**
```bash
git reset --soft <commit-hash>
git reset --hard <commit-hash>
```
**示例**
```bash
git reset --soft HEAD~1    # 软重置到上一个提交
git reset --hard HEAD~1    # 硬重置到上一个提交
```
`--soft` 只重置提交记录，`--hard` 会重置提交、暂存区和工作目录

## git stash
**作用**: 暂时保存当前的修改，清理工作目录
**用法**
```bash
git stash
git stash pop
```
**示例**
```bash
git stash       # 暂存当前更改
git stash pop   # 恢复暂存的更改
```

## git remote
**作用**: 查看或修改远程仓库的 URL
**用法**
```bash
git remote -v
git remote add <name> <url>
git remote remove <name>
```
**示例**
```bash
git remote -v                     # 查看远程仓库
git remote add origin https://github.com/user/repo.git    # 添加远程仓库
```

## git fetch
**作用**: 从远程仓库获取数据，但不会合并到当前分支
**用法**
```bash
git fetch <remote>
```
**示例**
```bash
git fetch origin
```
从远程仓库 `origin` 获取数据，不传拉取所有