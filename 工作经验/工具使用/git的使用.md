## git的使用

#### CRLF和LF 处理
- checkout时和提交时都用已有的换行符，不做替换
```
$ git config --global core.autocrlf false
```
- checkout时不转换，提交的时候自动转换为LF
```
$ git config --global core.autocrlf input
```

#### 克隆git的代码
```
git.exe clone --progress -v "https://git.oschina.net/wuxc_lx/iBase4J.git" "D:\github\iBase4J"
```
#### 更新上游仓库到远程git上的master分支
- 添加一个上版本库
```
git remote add upstream https://github.com/b3log/symphony.git
```
- 显示所有分之，并比较本地和远端分之版本
```
git branch -av
```
- 把上游的所有分支抓取过来
```
git fetch upstream
```
- 合并远程分支
```
git checkout master
git merge upstream/master
```
- 提交到主分支上
```
git push
```

####git如何切换远程仓库 
- 先保证本地代码是最新代码
```
 $ git pull -r
```
- 修改远程仓库地址
```
 $ git remote set-url origin http://bit.jd.com/bdpops/bdpops.git 
```


