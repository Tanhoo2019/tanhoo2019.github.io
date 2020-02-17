# 如何更新blog


## 新建博文

`hugo new posts/newblog.md`

打开新建的`newblog.md`，编辑blog内容

## 检查内容

cd 到blog根目录，然后输入以下命令：

`hugo server -D`

## 更新public静态页面

先cd到blog根目录，然后输入以下命令：

`hugo -D`

## 推送更新内容

cd到public目录下，然后输入以下命令：

```
git add -A
git commit -m "我的第二次提交"
git push -u origin master
```
















