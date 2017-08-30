### git的使用

**1.** git stash使用

   > git stash 命令简而言之就是帮助开发人员暂时搁浅当时已经做的改动，回退到改动之前的状态。

   > **A** 使用git add 把所有的改动添加到staging area.  COMMOND: git add .

   > **B** 使用git stash来搁置之前的改动

   > **C** 使用git stash list 来查看所有的搁置版本

   > **D** 取回第一个可以使用git stash pop

   > **E** 删除其中一个stash，使用命令git stash drop <id>

   > **F** 清空所有的stash， git stash clear