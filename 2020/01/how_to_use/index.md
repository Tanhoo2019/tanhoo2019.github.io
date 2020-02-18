# 如何更新blog


## 新建博文

`hugo new posts/newblog.md`

打开新建的`newblog.md`，编辑blog内容。

md编辑器我推荐用Typora，界面简单美观，还挺好用的。

## 检查内容

cd 到blog根目录，然后输入以下命令：

`hugo server -D`

## 更新public静态页面

先cd到blog根目录，然后输入以下命令：

`hugo -D`

## 推送更新内容

cd到public目录下，然后输入以下命令：

```
git add -A # 将public的所有更新内容添加到git暂存区
git commit -m "我的第二次提交" # 将暂存区文件提交到当前分支
git push -u origin master # 将本地版本库推到github的版本库（repository）
```



## 总结

往基于github的Hugo静态博客推送新博文的步骤分为以下几步：

1. 用hugo new命令新建md文件
2. 用hugo -D 生成public html 文件
3. 前往public目录
4. 用git add -A命令将全部更新的文件添加到暂存区
5. 用git commit 命令将暂存区内容添加到分支
6. 用git push 命令将分支内容推到github上去



如果想要更好地理解这个过程，可以去[廖雪峰的git学习网站](https://www.liaoxuefeng.com/wiki/896043488029600)上学，我就是从那边学的，很清晰。
















