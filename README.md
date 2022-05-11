

# GitTest

技术团队熟悉 Git 使用的仓库

## 加入项目

  - 注册 Github 就不再赘述；

  - 加入一个项目需要通过项目拥有人的邀请，邀请邮件会发送到邮箱，通过邮箱链接接受邀请；
    ![InkedSnipaste_2022-05-10_14-52-37_LI](https://user-images.githubusercontent.com/105333498/167761998-b66e44a2-4ad7-454f-ad81-ca8bfaa733b4.jpg)

  - 加入成功后，我们就可以在自己的 Github 首页看到自己的 `Repositories`;

    ![Inked167567672-4a2ee196-3eb9-430d-8ae0-c2def12f8a63_LI](https://user-images.githubusercontent.com/105333498/167762192-fcf1d8ff-e7ef-413c-9d98-7612cb48d800.jpg)

## 开始之前

在开始使用Git 之前，需要确保电脑已经安装了 Git，这里只讲 Windows 下的 Git 安装，MacOS已经系统自带 Git 了。

  - 下载 GIt，可以通过这个官方链接下载 [Git](https://git-scm.com/) ；

  - 下载后，安装默认点击`下一步`安装完成即可，具体的安装流程可以参考[这个](https://www.cnblogs.com/xueweisuoyong/p/11914045.html)；

  - 在 Github 进入工程后，点击 `Code`,可以看到 Git 的下载地址，这里有几个区别，`HTTPS` 的地址主要通过Github的邮箱和密码来验证权限；`SSH` 则通过一个在工程中加入的唯一的 SSH key 来验证权限。

  - 以通过账号密码来验证权限为例，拷贝 `HTTPS` 的 Git 地址：

  ![InkedSnipaste_2022-05-10_14-53-05_LI](https://user-images.githubusercontent.com/105333498/167762309-fb05d64a-d425-4b5a-8531-aac4ebf3ee54.jpg)

## 命令行操作

  ![bg2015120901](https://user-images.githubusercontent.com/94165481/167757863-13ee8f57-a7ce-4cc4-b67e-e033d3dbe88c.png)

`Windodws` 用户打开 `PowerShell`， `Mac` 用户打开 `终端`；

 - **查看用户 Git 信息**，用来查看登录的邮箱和地址：

   ```bash
   git config --list
   ```

   ![InkedSnipaste_2022-05-10_15-15-57_LI](https://user-images.githubusercontent.com/94165481/167757407-bf7ee75d-117c-483c-a4dc-fbae97094554.jpg)

   可以看到，当前的用户名和邮箱。如果不是你的GIthub的邮箱，那么可以通过下面的命令来修改。

 - **修改全局的用户名和邮箱**。

   ```bash
   # 设置提交代码时的用户信息
   $ git config [--global] user.name "[name]"
   $ git config [--global] user.email "[email address]"
   ```

   ![InkedSnipaste_2022-05-10_15-40-59_LI](https://user-images.githubusercontent.com/94165481/167757553-1bd23799-37fb-4dd3-89e3-6507cd79d21a.jpg)

   用户名和邮箱已经修改。

- **克隆项目**。下载项目代码：

  ```bash
  # 下载一个项目和它的整个代码历史
  $ git clone [url]
  ```

  ![Snipaste_2022-05-11_11-31-58](https://user-images.githubusercontent.com/105333498/167763698-945964f3-8fd3-4885-8afe-6d32abd99135.png)

  ![Snipaste_2022-05-11_11-32-48](https://user-images.githubusercontent.com/105333498/167763794-1e2b8f88-7979-4e8c-b983-1fd4f57ea91c.png)

  完成之后，文件夹中已经有相应的工程了，由于当前的工程只有默认的 `README.md` 的文件，我们可以来新建一个工程。

  ![Snipaste_2022-05-11_11-33-29](https://user-images.githubusercontent.com/105333498/167763859-20d2e670-7286-4306-9053-46689a7d551e.png)

- **添加代码到暂存区**。添加新建的工程代码：

  ```bash
  # 添加当前目录的所有文件到暂存区
  $ git add .
  # 显示有变更的文件
  $ git status
  ```

  ![Snipaste_2022-05-11_11-35-52](https://user-images.githubusercontent.com/105333498/167764092-58aa03a9-69bc-44cc-8e13-28c9c0b089ef.png)

- **提交代码**。提交暂存区的代码：

  ```bash
  # 提交暂存区到仓库区
  $ git commit -m [message]
  ```

  ![Snipaste_2022-05-11_11-37-09](https://user-images.githubusercontent.com/105333498/167764214-a8ed87b0-c599-4b20-bee7-5417e50cc2c2.png)
  目前代码已经成功提交到了暂存区，也就是说现在只是提交到了我们本地，接下来，我们需要将这部分代码推送到远程服务器，这样	其他的人也可以获取最新的代码。

- **查看分支**。在提交 Git 变化到远程服务器之前，我们来查看有远程有哪些分支：

  ```bash
  # 列出所有本地分支
  $ git branch
  # 列出所有远程分支
  $ git branch -r
  # 列出所有本地分支和远程分支
  $ git branch -a
  ```

  ![Snipaste_2022-05-11_11-38-13](https://user-images.githubusercontent.com/105333498/167764336-bb2e1078-ae23-4335-9feb-c90a636f4942.png)
  可以看到，本地当前分支为 `main`。远程分支目前有`main` 分支，这一般为主分支。我们当前是新建项目，那么就会推送到主分支。

- **推送远程分支**。

  ```bash
  # 上传本地指定分支到远程仓库
  $ git push [remote远程分支] [branch本地分支]
  ```

  ![Snipaste_2022-05-11_13-32-45](https://user-images.githubusercontent.com/105333498/167776131-93d65ede-7b28-4ad7-8b80-51b55f603a2c.png)
  打开 Github，发现我们已经成功的上传了我们的本地代码到远程服务器了。
  ![InkedSnipaste_2022-05-11_11-50-44_LI](https://user-images.githubusercontent.com/105333498/167776257-65898e88-4c86-4ac6-a5b5-53e3891a2402.jpg)
  **注意**，这里可能用人遇到无法上传的问题：
  ![Snipaste_2022-05-11_13-37-05](https://user-images.githubusercontent.com/105333498/167776358-fac8dd5a-6332-4502-ab54-fd056908544b.png)
  这可能是由于上传时 `HTTPS` 的验证导致的，可以切换为 `SSH` 的方式上传，或者关闭 `HTTPS`：`git config --global --unset http.proxy` 。再试试是否可以推送成功。

- **新增标签**。

  ```bash
  # 列出所有tag
  $ git tag
  # 新建一个tag在当前commit
  $ git tag [tag]
  # 提交所有tag
  $ git push [remote] --tags
  ```

  创建一个标签为 `1.0.1`的标签，并推送到远程分支。

  ![Snipaste_2022-05-11_13-40-46](https://user-images.githubusercontent.com/105333498/167776750-e2e4d69b-e29e-432d-920d-b2d655deecec.png)

   现在已经可以在 Github 主页看到相关的 `tag`：	![Snipaste_2022-05-10_16-42-52](https://user-images.githubusercontent.com/94165481/167587491-1f5dfe1f-544a-4a14-9d7b-fe67a0a39aa1.png)

- **分支**。在我们创建好 `main` 分支后，后续的开发都不会在 `main` 分支，一般会建立一个新的分支为 `develop` 。

  ```bash
  # 新建一个分支，但依然停留在当前分支
  $ git branch [branch-name]
  ```

  ![Snipaste_2022-05-11_13-48-37](https://user-images.githubusercontent.com/105333498/167777623-643e9ea3-53ce-4279-ba11-d807262656a3.png)

  已经创建一个名为 `develop` 的分支，但是当前还没有将本地的分支切换到 `develop`。

  ```bash
  # 切换到指定分支，并更新工作区
  $ git checkout [branch-name]
  ```

  ![Snipaste_2022-05-11_13-49-24](https://user-images.githubusercontent.com/105333498/167777714-e3ebe7dd-3108-447e-beaf-a25a81ad629e.png)

- **推送分支到远程**。

  ```bash
  # 推送本地分支到远程
  $ git push origin [branch-name]
  ```

  ![Snipaste_2022-05-11_13-50-37](https://user-images.githubusercontent.com/105333498/167777861-310cdf42-145e-4050-81e4-f8f52c91fbbb.png)

- **远程同步**。在我们已经成功的创建远程分支之后，一段时间之后，我们需要先同步远程的代码到本地。

  ```bash
  # 下载远程仓库的所有变动
  $ git fetch [remote]
  # 取回远程仓库的变化，并与本地分支合并
  $ git pull [remote] [branch]
  ```

  - `$ git fetch [remote]` 是用来将远程的代码拉取到本地，但是不和本地的代码合并，而是放在暂存区。
  - `git pull [remote] [branch]` 是将远程的代码拉取到本地，并且将代码和本地的代码合并。

- **合并分支**。当我们在分支开发了一个功能，现在测试通过需要把分支的代码合并到某个分支，比如合并 `develop` 分支到 `main` 分支：

  ```bash
  # 切换到主分支
  $ git checkout main
  # 主分支更新最新的代码
  $ git pull
  # 合并指定分支到当前分支
  $ git merge [branch]
  ```

   ![Snipaste_2022-05-11_13-52-56](https://user-images.githubusercontent.com/105333498/167778160-6b2361ed-b0e1-43a3-8620-09079de4f59a.png)
   ![Snipaste_2022-05-11_13-53-51](https://user-images.githubusercontent.com/105333498/167778292-9864ff2d-6f32-407a-844a-b5e6a6874eb3.png)

##  常用 Git 命令清单

### 新建代码库

```bash
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]
```

### 配置

Git 的设置文件为`.gitconfig`，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

```bash
# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

### 增加/删除文件

```bash
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```

### 代码提交

```bash
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```

### 分支

```bash
# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```

### 标签

```bash
# 列出所有tag
$ git tag

# 新建一个tag在当前commit
$ git tag [tag]

# 新建一个tag在指定commit
$ git tag [tag] [commit]

# 删除本地tag
$ git tag -d [tag]

# 删除远程tag
$ git push origin :refs/tags/[tagName]

# 查看tag信息
$ git show [tag]

# 提交指定tag
$ git push [remote] [tag]

# 提交所有tag
$ git push [remote] --tags

# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]
```

### 查看信息

```bash
# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
```

### 远程同步

```bash
# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all
```

### 撤销

```bash
# 恢复暂存区的指定文件到工作区
$ git checkout [file]

# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

# 恢复暂存区的所有文件到工作区
$ git checkout .

# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]

# 暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop
```

### 其他

```bash
# 生成一个可供发布的压缩包
$ git archive
```

## GUI 操作

目前市场几乎所有的 IDE 都集成了 Git 的 GUI。可以选择命令行操作，也可以使用一些第三方的 GUI 来管理 Git。常见的 Git 的 GUI 软件包含：[GitHub Desktop GitHub 官方客户端](https://desktop.github.com/) 、[SourceTree【推荐】](https://www.sourcetreeapp.com/) 、[Tower【好用但付费】](https://www.git-tower.com/windows) 、[SmartGit](https://www.syntevo.com/smartgit/) 、[Sublime Merge](https://www.sublimemerge.com/) 、[TortoiseGit](https://tortoisegit.org/)。

可以根据个人的使用习惯和偏好选择自己喜欢的GUI。目前我以最常用的 Git 软件 SourceTree 为例。

  ![Snipaste_2022-05-10_17-26-54](https://user-images.githubusercontent.com/94165481/167596601-44e0c2ed-1d15-42da-a5cd-0e466acc2d2f.png)

- **本地分支**，包含小圆点，并字体加粗的则是当前本地分支，可以看到当前分支为 `develop`：

  ![Snipaste_2022-05-10_17-28-39](https://user-images.githubusercontent.com/94165481/167596896-fb86fbaf-802a-40e1-8bb1-c176cd8143fd.png)

- **远程分支**：

  ![Snipaste_2022-05-10_17-30-12](https://user-images.githubusercontent.com/94165481/167597184-42709cc2-afea-4398-8a4f-ab558e2d2537.png)

- **标签**：

  ![Snipaste_2022-05-10_17-33-50](https://user-images.githubusercontent.com/94165481/167597934-9bc8298a-b46b-44b9-af27-c978d3099958.png)

- **提交历史**，可以在提交历史看到当前的分支、标签、远程分支、提交内容、提交日期、提交用户以及每个提交的哈希值：

  ![Snipaste_2022-05-10_17-36-05](https://user-images.githubusercontent.com/94165481/167598367-198b4c92-cbeb-4856-bfe2-c93d98a796aa.png)



- **修改文件**，待提交：

  1- 文件状态，查看当前修改的文件；
  
  2- 提交，待提交的文件数量等；
  
  3- 未暂存文件，还没有添加到暂存区的文件，提交前需先点击`暂存所有`，相当于命令 `git add .`。
  
  4- 文件修改内容；
  
  5- 提交的相关的内容；
  

  ![Snipaste_2022-05-10_17-42-01](https://user-images.githubusercontent.com/94165481/167599608-6b2a6e0c-cdf2-461c-a712-d90f3966db04.png)

- **添加文件到暂存区**。点击右侧"+"按钮添加文件到暂存区。查看哪些文件需要添加到本次提交，有些文件你修改来但还没有测试通过，所以暂未提交的话，就无需点击“+”。

  ![Snipaste_2022-05-10_17-39-48](https://user-images.githubusercontent.com/94165481/167600305-7298d4fb-aced-4923-8cb9-bd56769517a0.png)

- **提交更新**。在选择好了暂存文件后，并且输入了提交留言，可以点击**提交**按钮，那么就会将我们当前修改的内容更新到自己本地的Git 仓库中了。

- **快捷操作按钮**：

  - 提交，有文件更新需要提交；
  - 拉取，拉取远程仓库的代码并合并到代码中，相当于执行 `git pull [remote] [branch]`;
  - 推送，推送本地代码到远程仓库，相当于执行 `git push [remote] [branch]`;
  - 获取，获取远程仓库代码，但不合并到代码中，相当于执行 `git fetch [remote]` ；
  - 分支，创建一个新分支，相当于执行 `git checkout -b [branch]` ；
  - 合并，创建的分支需要合并到另一个分支，相当于执行 `git merge [branch]` ；
  - 贮藏，如果你有一些修改，但是你当前还不想提交到git上，但是你这个时候需要切换到另一个分支，那么你需要提交当前的变更或者丢弃当前的变更，这时候可以先点击贮藏，将文件的变更保留，下次再使用，相当于执行 ` git stash`；
  - 丢弃，重置自己对文件的修改等，相等于 `git reset [file]` ;
  - 标签，用来新增或删除相关的标签；

  ![Snipaste_2022-05-10_17-49-24](https://user-images.githubusercontent.com/94165481/167602766-50760279-db80-460c-ad3b-025359dfc557.png)
