### git学习记录

[TOC]

#### git commit

<img src="C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411200723443.png" alt="image-20250411200723443" style="zoom: 50%;" />

<img src="C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201006627.png" alt="image-20250411201006627" style="zoom: 67%;" />



#### git merge

<img src="C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201552274.png" alt="image-20250411201552274" style="zoom:50%;" />

 <img src="C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201610808.png" alt="image-20250411201610808" style="zoom: 80%;" />



![image-20250411201659469](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201659469.png)

![image-20250411201708809](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201708809.png)

#### git rebase

![image-20250411201754013](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201754013.png)

![image-20250411201852269](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201852269.png)

![image-20250411201916655](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201916655.png)

![image-20250411202004176](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411202004176.png)

根据继承关系  git rebase 可以作为分支引用向前移动的工具  **单参数 rebase 后面加的事目标分支的名称  而不是当前分支** 

git checkout <nameofbranch>; git merge <**要被合并的分支名字**，合并到的目标分支是当前分支>； git rebase <当前分支合并到的目标分支 即添加当前分支工作的那个分支名称>  在merge 和 rebase 过程中 ~~要注意理解不同提交的子集问题等等~~  **要用继承的思想去理解** 

#### git rebase

- rebase 复制分支到指定分支 
- git rebase <目标分支名> ~~一个参数即把分支复制当前HEAD所在分支 ？？？~~ 当前分支复制到目标分支
- git rebase <branch1 目标分支> <branch2被移动分支>  ~~两个参数 将branch1 复制到2 并checkout 至branch2~~
- 对于有继承关系的两个节点见的复制  只能是过去节点的前进

merge 合并 和 rebase 复制的

git branch <name>; git checkout <name_of_branch>; git checkout -b <name ofnew branch> （前两条命令的综合 即创建并更换到新的分支）

![image-20250411201143038](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201143038.png)

![image-20250411201231682](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201231682.png)

![image-20250411201430109](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411201430109.png)



#### git checkout <节点名即具体的提交记录比如C1>；  

#### 分离HEAD

HEAD 即引用 对当前所在分支的符号引用  要查看 HEAD 指向 使用 cat.git/HEAD 查看 

![image-20250411203717860](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411203717860.png)

分离的HEAD 怎么理解  指向具体的提交记录 而不是分支名

![image-20250411203918389](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411203918389.png)

#### **git checkout <--->^   理解相对引用 **

git checkout <--->^

![image-20250411204044980](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204044980.png)

![image-20250411204101880](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204101880.png)

相对引用 可以跟在任意一个 名称或者可以作为参考位置的名称后面  通常执行的事向上方的提交记录移动

![image-20250411204126582](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204126582.png)

^ 向上移动一格提交记录  ~<num> 向上移动（后退）N个提交记录；git checkout HEAD~4; git checkout 

![image-20250411204736040](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204736040.png)

git branch -f main HEAD~3; 让分支main 强制指向HEAD的第三级parent提交；

![image-20250411204755937](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204755937.png)

<img src="C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204842711.png" alt="image-20250411204842711" style="zoom:67%;" />

![image-20250411204902892](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411204902892.png)



#### 撤销 本地分支与远程分支的撤销

git reset HEAD~<NUM>; 本地分支中的撤销，撤销至HEAD的第N级parent节点

git revert HEAD; 远程分支的撤销，提交一个与HEAD上一个状态相同的提交记录

![image-20250411205045915](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411205045915.png)

![image-20250411205109743](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411205109743.png)



#### **关于提交--移动**

![image-20250411205237714](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411205237714.png)



git cherry-pick <bei合并的提交号> 多个不同分支提交记录的合并移动  **一次移动到当下HEAD指向的地方** 

![image-20250411210131853](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411210131853.png)

这里提到了提交记录的哈希值 其实就是节点的位置 节点名称

![image-20250411210443255](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411210443255.png)

git rebase -i <需要交互修改的提交记录点>; e.g. git rebase -i HEAD~4;(当前第四个parent之后的提交记录) 整理提交记录

UI交互界面来移动提交记录 

![image-20250411210638101](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411210638101.png)



#### **提交技巧**

想要修改前面提交过程中的细节 使用 git rebase -i 交互式更改顺序 不仅可以更改顺序 还可以隐藏或者消除提交记录

![image-20250411211158490](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411211158490.png)

技巧1

![image-20250411212052760](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411212052760.png)

![image-20250411212117700](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411212117700.png)

技巧2

使用 git cherry-pick ----   可以pick任何东西

![image-20250411212632181](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411212632181.png)

#### git tag 和 git describe

![image-20250411214543807](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411214543807.png)

![image-20250411214557014](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411214557014.png)



**rebase 分支的复制 将分支的整条提交记录复制下来 即把存在差异的提交记录都复制到目标分支下面 **

![image-20250411215944071](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411215944071.png)

#### 两个父节点 两个parent  ^后面跟数字

![image-20250411220208455](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411220208455.png)

![image-20250411220328662](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250411220328662.png)

git branch <新建立的分支名> <目标节点位置>

git cherry-pick 的用法核心 移动到当下HEAD指向  因此 首先要将HEAD移动到你想要的位置 即使用 git checkout 

git rebase -i HEAD~<num> 的核心也是找到合适的HEAD指向   将one移动到合适的位置  即使用 git rebase main one;

![image-20250412004645820](C:\Users\liuwei\AppData\Roaming\Typora\typora-user-images\image-20250412004645820.png)

git提交树：~~提交树是什么？~~  提交历史记录  下面的命令即为提交树上的**移动操作**  **节点的切换  **

head：理解成指向当前修改提交记录的一个即时指针 而main是提交记录的内存位置编号  **head 与 分支main或者bugFix的关系是什么**   **分离的HEAD 和 没分离的HEAD有什么异同和特征作用**

​	- 对当前所在分支的符号引用（**怎么理解引用**）---即指向  你正在其基础上  进行工作  的提交记录

​	- 通常情况下**指向分支名**（改变分支状态的变化可以通过head变得可见）git checkout C1; git checkout main; git commit; git checkout C2

​	- 分离的 head ：指向某个具体的提交记录 而不是 分支名   git checkout C1 

​	**通过哈希值指定提交记录 每个提交记录的哈希值显示在代表提交记录的圆圈中 ？？**

相对引用：？对概念存疑   （通过 指定 提交记录哈希值 的方式在 Git 中移动）在易于记忆的地方开始计算 （相对某个节点）

​	^ 操作符：加在引用名称的后面 ---> 让Git 寻找指定提交记录的 parent 提交，即 main^ ----> main 的 parent 节点 main^^ --- > 第二个 parent 节点



![image-20250411111613218](D:\01tempfiles\002git学习记录\main的parent节点.png)

​    

![main的parent节点2](D:\01tempfiles\002git学习记录\main的parent节点2.png)

这里main的parent节点是哪一个  解答 父节点 可以理解成上一个提交记录  提交变更的基础
