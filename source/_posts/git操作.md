---
title: git操作
date: 2021-11-25 19:03:51
tags:
---
## 1.基础和常用命令
git三个区域（工作区，暂存区（git add),版本库(git commit )
1.git init,git status,git add .,git commit -m 'jilu',git config --global user.email,git config --global user.name
2.git log/reflog .   git reset --hard '提交编号'

## 2.添加到远程
第一次添加到远程：
git init
git remote add origin https://github.com/feixiangsnaik/feixiangsnaik.io.git
git pull --rebase origin main
git push -u origin main

## 常见报错
二、常见报错处理
1、导致报错:error: You have not concluded your merge (MERGE_HEAD exists).的原因可能是在以前pull下来的代码自动合并失败。
　　解决方案一：保留本地的更改，中止合并->重新合并->重新拉取
$:git merge --abort
$:git reset --merge
$:git pull
　　git pull之后然后重新解决冲突，再push，（记得需要稍微跟自己push的要有一点区别，要不然又会造成这样的情况）
　　解决方案二：舍弃本地代码，远端版本覆盖本地版本（慎重）
$:git fetch --all
$:git reset --hard origin/master
$:git fetch
2、Git fetch和git pull的区别
　　都可以从远程获取最新版本到本地
　　git fetch：只是从远程获取最新版本到本地，不会merge(合并)
$:git fetch origin master   //从远程的origin的master主分支上获取最新版本到origin/master分支上
$:git log -p master..origin/master //比较本地的master分支和origin/master分支的区别
$:git merge origin/master          //合并
　　Git pull：从远程获取最新版本并merge(合并)到本地
$:git pull origin master  //相当于进行了 git fetch 和 git merge两部操作
3、本地删除无效的远程分支：清理远程分支，把本地不存在的远程分支删除
git remote prune origin

## 代码回退等
git提交之后没有push，代码被覆盖之后恢复
git  reflog  通过这个看commit id
git reset [commit id] --hard   有时候要删除一个index.lock文件。
//git 强制拉代码
git fetch --all
git reset --hard origin/master
git pull //可以省略