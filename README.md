# GitBook操作说明
当访问 https://freefuncode.github.io/GitBook/ 时，会访问 FreeFunCode/GitBook 项目的 gh-pages 分支的内容，所以需要为项目创建一个 gh-pages 分支，并且将静态站点内容放入其中。也就是说，GitBook 项目将有如下两个分支：

master, 保存书籍的源码
gh-pages, 保存书籍编译后的 HTML 文件

--------

## master

1. 切换分支 `git checkout master`

2. 编写书籍

3. 生成_book静态文件`gitbook build`

4. 启动本地服务`gitbook serve`

5. 浏览器输入：`localohost:4000` 验证

6. 提交源码到master分支
```
git add .
git commit -m "push source code"
git push origin master
```
--------

## gh-pages

  1. 切换分支到gh-pages，并且删除分支下旧文件

```
git checkout gh-pages
git rm -f --cached -r .
git clean -df
rm -rf *~
```
   2. 目录下应该只剩下 _book 目录了，添加忽略文件.gitignore

```
echo "*~" > .gitignore
echo "_book" >> .gitignore
git add .gitignore
git commit -m "Ignore some files"
```
3. 加入 之前编译的_book 下的内容到分支gh-pages，并提交。

```
cp -r _book/* .
git add .
git commit -m "Publish book"
git push -u origin gh-pages
```

--------

## 目录收缩插件：expandable-chapters-small
book.json:
```
{
 
    "plugins": [
        "expandable-chapters-small@^0.1.7"
    ]
}
```
`gitbook install`
 



