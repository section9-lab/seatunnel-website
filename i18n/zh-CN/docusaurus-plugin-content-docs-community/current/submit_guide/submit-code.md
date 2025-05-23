---
title: 提交代码
sidebar_position: 2
---

# 提交代码

* 首先从远端仓库 <https://github.com/apache/seatunnel.git> fork一份代码到自己的仓库中

* 远端仓库中目前有三个分支：
    * **dev**    日常开发分支
    > 日常dev开发分支，新提交的代码都可以pull request到这个分支上。

    * **2.3.9-release** 发布版本分支
    > 发布版本分支，后续会有3.0...等版本分支。

* 以您fork的仓库命名为`seatunnel`为例

* 把自己仓库clone到本地

    ```shell
    git clone git@github.com:<YOUR_GITHUB_ID>/seatunnel.git
    ```

* 添加远端仓库地址，命名为upstream

    ```shell
    git remote add upstream git@github.com:apache/seatunnel.git
    ```

* 查看仓库：

    ```shell
    git remote -v
    ```

  > 此时会有两个仓库：origin(自己的仓库)和upstream（远端仓库）

* 获取/更新远端仓库代码（已经是最新代码，就跳过）

    ```shell
    git fetch upstream
    ```

* 同步远端仓库代码到本地仓库

    ```shell
    git checkout origin/dev
    git merge --no-ff upstream/dev
    ```

* 创建一个新的分支来修改代码

    ```shell
    git checkout -b feature-xxx
    ```

* 在本地修改代码以后，提交到自己仓库：

    ```shell
    git commit -m 'commit content'
    git push
    ```

* 将修改提交到远端仓库

    * 在 GitHub 的 PullRequest 页面，点击 "New pull request".

    * 选择修改完的本地分支和要合并的目的分支，点击 "Create pull request".

* 接着社区 Committer 们会做 CodeReview，然后他会与您讨论一些细节（包括设计，实现，性能等）。当团队中所有人员对本次修改满意后，会将提交合并到dev分支

* 最后，恭喜您已经成为了 Apache SeaTunnel 的官方贡献者！
