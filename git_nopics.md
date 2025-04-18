git commit;

git merge

git rebase

根据继承关系  git rebase 可以作为分支引用向前移动的工具  **单参数 rebase 后面加的事目标分支的名称  而不是当前分支**

- rebase 复制分支到指定分支 
- git rebase <目标分支名> ~~一个参数即把分支复制当前HEAD所在分支 ？？？~~ 当前分支复制到目标分支
- git rebase <branch1 目标分支> <branch2被移动分支>  ~~两个参数 将branch1 复制到2 并checkout 至branch2~~
- 对于有继承关系的两个节点见的复制  只能是过去节点的前进
- **rebase 分支的复制 将分支的整条提交记录复制下来 即把存在差异的提交记录都复制到目标分支下面 **

git checkout <nameofbranch>; 

git merge <**要被合并的分支名字**，合并到的目标分支是当前分支>；   **把某分支合并到当前分支**

git rebase <当前分支合并到的目标分支 即添加当前分支工作的那个分支名称>  **把当前分支合并到某分支**

在merge 和 rebase 过程中 要注意理解不同提交的子集问题等等  

git branch <name>; 

git checkout <name_of_branch>; 

git checkout -b <name ofnew branch> （前两条命令的综合 即创建并更换到新的分支）

git checkout <节点名即具体的提交记录比如C1>；  

HEAD 即引用 对当前所在分支的符号引用  要查看 HEAD 指向 使用 cat.git/HEAD 查看

分离的HEAD 怎么理解  指向具体的提交记录 而不是分支名

git checkout <--->^

- 相对引用 可以跟在任意一个 名称或者可以作为参考位置的名称后面  通常执行的事向上方的提交记录移动
- ^ 向上移动一格提交记录  ~<num> 向上移动（后退）N个提交记录；git checkout HEAD~4; git checkout 
- git branch -f main HEAD~3; 让分支main 强制指向HEAD的第三级parent提交；

撤销 本地分支与远程分支的撤销

- git reset HEAD~<NUM>; 本地分支中的撤销，撤销至HEAD的第N级parent节点
- git revert HEAD; 远程分支的撤销，提交一个与HEAD上一个状态相同的提交记录

**关于提交--移动**

- git cherry-pick <bei合并的提交号> 多个不同分支提交记录的合并移动  **一次移动到当下HEAD指向的地方** 
- 这里提到了提交记录的哈希值 其实就是节点的位置 节点名称
- git rebase -i <需要交互修改的提交记录点>; e.g. git rebase -i HEAD~4;(当前第四个parent之后的提交记录) 整理提交记录   UI交互界面来移动提交记录 
- git cherry-pick 的用法核心 移动到当下HEAD指向  因此 首先要将HEAD移动到你想要的位置 即使用 git checkout 
- git rebase -i HEAD~<num> 的核心也是找到合适的HEAD指向   将one移动到合适的位置  即使用 git rebase main one;

**提交技巧**

- 想要修改前面提交过程中的细节 使用 git rebase -i 交互式更改顺序 不仅可以更改顺序 还可以隐藏或者消除提交记录
- 使用 git cherry-pick ----   可以pick任何东西

git tag 和 git describe

两个父节点 两个parent  ^后面跟数字 来区分上移到哪个父节点

git branch <新建立的分支名> <目标节点位置>



