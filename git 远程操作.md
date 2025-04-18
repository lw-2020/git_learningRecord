git 远程操作

git clone  在本地创建一个远程仓库的拷贝

<remote name>/<branch name> 远程分支的命名规范

​	git checkout origin/main; git commit 这条命令会让Git编程分离的HEAD状态  当添加新的提交时 origin/main 也不会更新 这是因为 origin/main 只有在远程仓库中相应的分支更新了以后才会更新  这里不是很懂

![image-20250412102633256](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250412102633256.png)

远程分支是什么 比如origin/main 远程分支的属性切换到远程分支时 自动进入分离HEAD状态 

远程分支的命名规范：<remote name>/<branch name> 即远程仓库的名称时 origin 

远程仓库

- git clone 后本地仓库中多了o/main 分支 即远程分支
- 反映的是远程仓库的状态（此状态是你上次与它通信时的状态）
- 切换到远程分支 会自动分离HEAD，因为你的本地提交不能直接提交到远程分支上

git fetch  **实际上是将本地仓库中的远程分支更新成了远程仓库在你最后一次 与他通信时的状态    是你与远程仓库通讯你的方式**

git fetch 并不会改变本地仓库的状态 不会更新main分支 不会修改磁盘文件

-  从远程仓库下载本地仓库缺失的提交记录
- 更新远程分支指针（origin/main）
- `git fetch` 通常通过互联网（使用 `http://` 或 `git://` 协议) 与远程仓库通信。



git pull 当远程分支中有新的提交时 可以像合并本地分支那样来合并远程分支  git fetch 和 git merge 的结合  和远程仓库的通信 避免发生冲突

应用场景：需要提出一个 pull request 时，直接提交（提起了一个commit）到本地的 main 然后试图推送（提起一个push）修改 这种情况会被远程服务器拒绝，并提示必须使用pull request 来更新分支

git branch -f main o/main  强制移动main 到 o/main

git checkout -b feature C2  新建 feature 在C2 节点上

git push origin feature  推送 feature 到远程仓库

![image-20250418183928267](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250418183928267.png)



![image-20250412162140905](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250412162140905.png)

![image-20250412162201272](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250412162201272.png)

合并特征分支

- 将特征分支集成到 main 上
- 推送并更新远程分支

![image-20250412194136194](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250412194136194.png)



分支的 remote tracking 属性？跟踪分支 某分支推送到远程仓库后 本地生成的跟踪分支

main和o/main之间的相关性 

- pull （fetch 和 merge 操作）操作时, 提交记录会被先下载到 o/main 上，之后再合并到本地的 main 分支。隐含的合并目标由这个关联确定的。
- push 操作时, 我们把工作从 `main` 推到远程仓库中的 `main` 分支(同时会更新远程分支 `o/main`) 。这个推送的目的地也是由这种关联确定的！
- main 和 o/main 的关联关系 是由 remote tracking 属性决定的，main 被设定为跟踪o/main  即main分支制定了推送的目的地 以及 拉取后的目标
- 可以让任意分支跟踪 `o/main`, 然后该分支会像 `main` 分支一样得到隐含的 push 目的地以及 merge 的目标。 这意味着你可以在分支 `totallyNotMain` 上执行 `git push`，将工作推送到远程仓库的 `main` 分支上。
- 在 notmain 分支上执行 push 操作可以将工作推送到 main 分支上





git push 的参数

git push <remote> <place>

gi push origin  main  

- *切到本地仓库中的“main”分支，获取所有的提交，再到远程仓库“origin”中找到“main”分支，将远程仓库中没有的提交记录都添加上去，搞定之后告诉我。*
- 我们通过“place”参数来告诉 Git 提交记录来自于 main, 要推送到远程仓库中的 main。它实际就是要同步的两个仓库的位置。
- 需要注意的是，因为我们通过指定参数告诉了 Git 所有它需要的信息, 所以它就忽略了我们所切换分支的属性！

远程跟踪



git checkout -b <new branch_totally not main> o/main;  这里创建的totally not main分支具备了跟踪远程分支的属性 (可以 git pull; git commit; git push 试验一下)

git branch -u o/main <totally_not_main>; 如果当前就在 totally_not_main 分支上，可以直接写 git branch -u o/main 

git push origin <place>    关注place参数

- git push origin main   main 给出了推送过的来源和目的地

- git push origin <source>:<destination>
- <source>为空的情况 git push origin :<destination>; git fetch origin :<destination>

git pull origin <destination>

git pull origin <>:<destination>









