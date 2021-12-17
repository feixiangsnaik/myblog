---
title: hexo操作
date: 2021-12-16 16:22:03
tags:
---
## 发布命令
    hexo clean && hexo g && hexo d
## 新建文章
    hexo new articleTest
## 搭建步骤
//第一条   安装hexo的基础框架，如果很慢的话，可以考虑挂下梯子，或者换个源
     npm install -g hexo
     
     //第二条   初始化hexo框架 这个可能会比较慢
     hexo init
     
     //第三条 安装所需要的组件
     npm install
     
     //第四条 编译生成静态页面
     hexo g
     
     //第五条 启动本地服务
     hexo s

合并：1.     npm install -g hexo && hexo init && npm install &&npm i hexo-deployer-git && hexo g && hexo s 
git 步骤：2.git config --global user.name 'feixiangsnaik' &&git config --global user.email 'feixiangsnail@gmail.com'&&ssh-keygen -t rsa -C 'feixiangsnail@gmail.com'    然后回车到底，把pub的内容拷贝到github ssh里面。
3.deploy:
  type: git
  repository: https://github.com/feixiangsnaik/feixiangsnaik.github.io
  branch: master
把上面代码添加到config.xml最下面
4.hexo new post "article title"新建文章，然后 hexo g && hexo s &&hexo d（或者清除缓存，每次修改配置文件后都要执行该命令
  hexo clean
  
  // 生成静态页面文件，每次clean后也要重新生成
  hexo g
  
  // 向仓库推送文件
  hexo d）
合并：hexo clean && hexo g && hexo d