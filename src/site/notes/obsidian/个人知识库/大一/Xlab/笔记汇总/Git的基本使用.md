---
{"dg-publish":true,"permalink":"/obsidian///xlab//git/","created":"2024-09-05T15:38:57.787+08:00","updated":"2024-09-08T15:25:05.482+08:00"}
---

# 个人学习体会
对于并不复杂的结构处理，日常可以用Github Desktop来替代命令行操作

# 思考题

## - [easy] 如何合并多个commit至一个？会有什么副作用？

-  `git rebase -i HEAD~n` 其中n为需要合并的提交数量
- **副作用**：
	- 合并提交会丢失提交历史，可能影响问题追踪。比如与之前提交进行比较以排查问题所在时，需要对多次提交的合并检查更多细节
	- 强制合并后，协作者基于之前分布提交的分支会产生冲突

## - [easy] git reset --hard --soft --mixed 有什么区别？一般用哪个？

- `--soft`：只回退 HEAD 指针，暂存区（index）和工作目录不会改变。代码仍然保留在暂存区，可以直接重新提交。
- `--mixed`（默认）：回退 HEAD 和暂存区，工作目录不变。即修改还在工作目录中，但从暂存区中移除。
- `--hard`：回退 HEAD、暂存区和工作目录，所有未提交的修改都会被删除，工作目录回到指定 commit 的状态。
一般使用默认的mixed, 如果确定暂存的修改需要保留，则使用`git reset --soft`。

## - [easy] git reset --hard [sha of some earlier commit] 后，git log中最新几个commit消失。此时如何回到之前的最先commit？你觉得git log和git reflog有何区别？

- 通过`git reflog`查看HEAD指针的操作，通过`git reset --hard [SHA]`回到指定的commit
- `git log` 只显示当前分支的提交历史，不会显示被隐藏的提交历史
- `git reflog` 显示本地仓库所有的提交记录，便于恢复指定版本

## - [advanced] 目前有三个连续的commit ABC，希望将C关于B的修改应用于A上并新建分支。如何做到？

### 方法一：
1. 创建新的分支A
	`git checkout -b new-branch A`
2. 查看C相对于B，并决定将差异运用到B上
	`git diff ` B C | git apply
3. 提交修改
```bash
git add .
git commit -m "push"
```

### 方法二：
```bash
git checkout -b new-branch A
git cherry-pick C
```


