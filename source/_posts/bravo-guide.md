title: Bravo周刊投稿指南
date: 2015-09-18 20:35:19
tags:
---
Bravo周刊源码托管在github上，同时结合github的gh-pages能力和hexo飞一般的静态blog管理功能，让投稿者可以专注于用markdown完成文章内容，而不需要关心blog其他资源的管理，只需几行命令便可轻松搞定。噢耶，bravo！
<!-- more -->
## 安装git
已安装的用户请跳过此步骤。
- windows用户
[Github Windows](https://desktop.github.com/) 
- mac用户
 [Github Mac](http://git-scm.com/download/mac) 
## 安装Node.js
[Node.js install](https://nodejs.org/download/)
## 安装hexo
``` { .theme-peacock }
npm install hexo-cli -g
```
 
## 新建文章
- 拉取代码
``` { .theme-peacock }
git clone https://github.com/tbbravo/tbbravo.github.io.git
# 克隆tbbravo.github.io到本地
git branch
# 查看所有分支
git checkout source
# tbbravo.github.io有master和source两个分支，source分支用于存放hexo源码，master用于存放由hexo生成的public中的发布到页面中的代码。注：所有修改都应在在source分支下进行，master分支只用于存放source生成的发布代码！
cd tbbravo.github.io
# 进入tbbravo.github.io目录
```

- 初始化hexo配置
``` { .theme-peacock }
hexo init

#安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
hexo init
npm install

#新建完成后，指定文件夹的目录如下
.
├── _config.yml
├── package.json
├── scaffolds
├── scripts
├── source
|      ├── _drafts
|      └── _posts
└── themes
```

- 新建一篇文章
``` { .theme-peacock }
hexo n 'article1' 
# hexo new 的简写
# 执行完后，将会在tbbravo.github.io/source/_posts目录下生成article1.md
```

- 编辑文章内容
``` { .theme-peacock }
vi tbbravo.github.io/source/_posts/article1.md
```

- 编译生成html
``` { .theme-peacock }
hexo g
# hexo generate 的简写
# 执行完后，将生成public目录，内容是根据hexo的theme和article1.md生成的html等文件
```

## 发布文章
- 拷贝public文件
``` { .theme-peacock }
git clone --depth 1 --branch master --single-branch . || (git init && git remote add -t master origin )
rm -rf ./*
cp -r ../public/* .
# 将source分支下生成的public下的所有内容copy到master根目录下
```

- 提交master目录
``` { .theme-peacock }
git commit -m 'your comment'
# 提交修改
git push
# 发布到master分支
```

## 预览效果
提交成功后，大概等上1分钟左右，访问[这里](http://tbbravo.github.io/)查看效果
## 提交source分支代码
完成新文章的投稿后，需要提交原来在source分支下用markdown编写的内容
``` { .theme-peacock }
git branch
# 查看自己当前在哪个繁殖下
git checkout source
# 切换到source分支下
git add -A
# 添加所有新增内容
git commit -m 'your comment'
# 提交修改
git push origin source
# 发布到source分支
```

## The end. Contact @regrex