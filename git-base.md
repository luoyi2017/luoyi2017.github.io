# Git学习笔记
## 日期：2017-06-07
---
#### 6个常用命令：  
![201706101049](images\2017\201706101049.png) 
注：Workspace工作区； Index/Stage暂存区； Repository仓库区（或本地仓库）； Remote远程仓库；

#### 新建代码库
```
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]
```







---
强推，即利用强覆盖方式用你本地的代码替代git仓库内的内容
git push -f
#### `git init` 初始化
```
$ git init
```
#### `git add` 开始对文件进行跟踪
```
git commit              提交
git clone [url]         克隆仓库
git branch newImage     创建新分支newImage
git checkout newImage   切换到新分支newImage
git checkout -b <your-branch-name>  创建一个新的分支同时切换到新创建的分支
```
```
$ git commit -m 'initial project version'

$ git clone git://github.com/schacon/grit.git
这会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录，然后从中取出最新版本的文件拷贝。
```
#### 参考资料
[Git - Book](https://git-scm.com/book/zh/v1)
