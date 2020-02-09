# 常用命令

## GIT

* tag

  ```
  # 列出现有标签
  git tag

  # 查看相应标签的版本信息
  git show v0.1

  # 新建标签
    ##建轻量级标签，例如标签v0.1
    git tag v0.1
    
    ##含附注的标签，需要加-a指定标签，-m指定附注内容
    git tag -a v0.1 -m "my version 1.4"
    
    ##签署标签，将-a改成-s。注意，这需要私钥
    git tag -s v0.1 -m "my version 1.4"
    
    ##验证标签，加-v。注意:需要有签署者的公钥
    git tag -v v0.1
    
  #将标签推送到远端服务器
  git push origin v0.1
   
   ##一次性推送所有新增的本地标签到远端
   git push origin --tags
    
    
    
  ```

* 提交修改

  ```
  ###修改完成后用add
  git add .
  ### 查看修改的文件列表
  git status
  ### 查看不在缓冲区的文件发生的改变
  git diff 或者 git diff filename
  ### 查看缓冲区的文件发生的改变
  git diff --cached或者git diff --staged
  ### 本地提交
  git commit -m "add a comment"
  
  
  
  
  
  
  ```

  

  

* 查看本地和远程分支的关系

  ```
  #列出所有本地分支和远程分支
  git branch -vv
  
  #本地分支与远程分支的差集 :（显示远程有而本地没有的commit信息）
  git log master   origin/master
  ```







## 解压缩

* 解压

  ```
  ##tar.gz格式
  tar -xzf  example.tar.gz
  ```


## Linux

* find

  ```
  ##查找包含指定内容的文件
  find / | xargs grep function 查找系统根目录下面的所有文件的内容中包含有function字符串的文件列表。
  
  find .|xargs grep x
  find . -exec grep x{} \;
  
  find / -name "httpd.conf"
  
  find / -name "rsync"
  
  为什么会这样能，因为通道命令符是把上一部的结果传递给下一步来处理，在 find . |grep x中虽然看似和find .|xargs grep x差不多，但是实际上还是有区别的。应为find .得到的结果是一串文件名集合，如果直接传递给grep的话，grep会把这些文件名看作一些无意义的字符串来处理。但是传递给xargs，他会把他当作一个有意义的文件来处理。
  ```

* screen

  ```
  ##列出所有session
  screen -ls
  ##开始一个session
  screen -S  session_name
  
  ##进入一个session
  screen  -r  session_id或者name
  如果这个session已经被进入即在attated状态，那么用如下命令
  screen -D -r session_id或者name 
  ##kill一个session
  screen -S session_name -X quit
  
  ##退出当前session，但并不关闭这个session
在每个screen session 下，所有命令都以 ctrl+a(C-a) 开始。
  先按ctrl+a 然后按d
  
  ```
  
* grep

  * 输出不同的行：
    grep -v -wvf file1 file2  

    输出相同的行：
    grep -wf file1 file2

## Docker

* 批量清除容器，镜像，卷

```
##清除容器
docker rm -f $(docker ps -qa)
##清除镜像
docker rmi -f $(docker images -q)
##清除卷
docker volume rm $(docker volume ls -q)
```

