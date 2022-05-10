

# Snail_Git_test

Snail 技术团队熟悉 Git 使用的仓库

## 加入项目

  - 注册 Github 就不再赘述；

  - 加入一个项目需要通过项目拥有人的邀请，邀请邮件会发送到邮箱，通过邮箱链接接受邀请；
    ![Snipaste_2022-05-10_14-52-37](https://user-images.githubusercontent.com/94165481/167567187-045cb732-af5a-43ed-9c17-52dba6fd28fa.png)

  - 加入成功后，我们就可以在自己的 Github 首页看到自己的 `Repositories`;

    ![Snipaste_2022-05-10_15-00-38](https://user-images.githubusercontent.com/94165481/167567672-4a2ee196-3eb9-430d-8ae0-c2def12f8a63.png)

## 获取代码

  - 在 Github 进入工程后，点击 `Code`,可以看到 Git 的下载地址，这里有几个区别，`HTTPS` 的地址主要通过Github的邮箱和密码来验证权限；`SSH` 则通过一个在工程中加入的唯一的 SSH key 来验证权限。

  - 以通过账号密码来验证权限为例，拷贝 `HTTPS` 的 git 地址：

    ![Snipaste_2022-05-10_14-53-05](https://user-images.githubusercontent.com/94165481/167568895-20289c9b-e166-475c-a5d6-2ff83bc118aa.png)

 - `Windodws` 用户打开 `PowerShell`， `Mac` 用户打开 `终端`；

 - 查看用户Git信息，用来查看登录的邮箱和地址：

   ```bash
   git config --list
   ```

   ![Snipaste_2022-05-10_15-15-57](https://user-images.githubusercontent.com/94165481/167571088-efe74c8f-29d1-4cb8-8ce5-260bcf798947.png)

   可以看到，当前的用户名和邮箱。如果不是你的GIthub的邮箱，那么可以通过下面的命令来修改。

 - 修改全局的用户名和邮箱：

   ```bash
   # 设置提交代码时的用户信息
   $ git config [--global] user.name "[name]"
   $ git config [--global] user.email "[email address]"
   ```

   ![Snipaste_2022-05-10_15-40-59](https://user-images.githubusercontent.com/94165481/167575428-7a2f146e-a441-40ec-8dfa-5fd1238a0a5f.png)

​		用户名和邮箱已经修改。

- 克隆项目。下载项目代码：

  ```bash
  # 下载一个项目和它的整个代码历史
  $ git clone [url]
  ```

  ![Snipaste_2022-05-10_15-45-40](https://user-images.githubusercontent.com/94165481/167576199-89766902-9f40-4c4a-a9cb-9f1ccf62ee7e.png)

![Snipaste_2022-05-10_15-46-30](https://user-images.githubusercontent.com/94165481/167576365-df6f09ca-2a78-4a3f-b317-2bc487abfe2f.png)

​		完成之后，文件夹中已经有相应的工程了，由于当前的工程只有默认的 `README.md` 的文件，我们可以来新建一个工程。

​		![Snipaste_2022-05-10_15-53-10](https://user-images.githubusercontent.com/94165481/167577650-c9e523d1-7f4d-48de-b966-9dff9be7dd78.png)

- 添加代码到暂存区。添加新建的工程代码：

  ```bash
  # 添加当前目录的所有文件到暂存区
  $ git add .
  # 显示有变更的文件
  $ git status
  ```

  ![Snipaste_2022-05-10_15-56-16](https://user-images.githubusercontent.com/94165481/167578226-9b3aa951-bf04-49f5-9678-ab390610ba95.png)

- 提交代码。提交暂存区的代码：

  ```bash
  # 提交暂存区到仓库区
  $ git commit -m [message]
  ```

  ![Snipaste_2022-05-10_16-02-51](https://user-images.githubusercontent.com/94165481/167579465-1b38692b-d39c-4ed8-8d8f-b9fce2b73b4c.png)

​	目前代码已经成功提交到了暂存区，也就是说现在只是提交到了我们本地，接下来，我们需要将这部分代码推送到远程服务器，这样其他的人也可以获取最新的代码。

- 查看分支。在提交 git 变化到远程服务器之前，我们来查看有远程有哪些分支：

  ```bash
  # 列出所有本地分支
  $ git branch
  
  # 列出所有远程分支
  $ git branch -r
  
  # 列出所有本地分支和远程分支
  $ git branch -a
  ```

  ![Snipaste_2022-05-10_16-08-39](https://user-images.githubusercontent.com/94165481/167580610-5efa632d-ab4b-405a-987e-b4e8a12425fe.png)

​	可以看到，本地当前分支为 `main`。远程分支目前有`main` 分支，这一般为主分支。我们当前是新建项目，那么就会推送到主分支。

- 推送远程分支。

  ```bash
  # 上传本地指定分支到远程仓库
  $ git push [remote远程分支] [branch本地分支]
  ```

​		![Snipaste_2022-05-10_16-28-47](https://user-images.githubusercontent.com/94165481/167584596-a9ae53b0-9728-4cf4-828e-1297acf425db.png)

​		打开Github，发现我们已经成功的上传了我们的本地代码到远程服务器了。

![Snipaste_2022-05-10_16-29-39](https://user-images.githubusercontent.com/94165481/167584751-88ffc47f-445a-459f-a886-79af1954c382.png)

​		**注意**，这里可能用人遇到无法上传的问题：

​		![Snipaste_2022-05-10_16-36-43](https://user-images.githubusercontent.com/94165481/167586234-49e6d7ac-a437-40fd-89ea-2b382390dde6.png)

​		![Snipaste_2022-05-10_16-31-31](https://user-images.githubusercontent.com/94165481/167585165-9ad1458c-4dfb-49e1-87f8-91887dc691ca.png)

​		这可能是由于上传时 `HTTPS` 的验证导致的，可以切换为 `SSH` 的方式上传，或者关闭 `HTTPS`：`git config --global --unset http.proxy` 。再试试是否可以推送成功。

- 新增标签。

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

  创建一个标签为 `1.0.0`的标签，并推送到远程分支。

  ![Snipaste_2022-05-10_16-41-39](https://user-images.githubusercontent.com/94165481/167587209-c1caa3e9-79c2-4514-82bd-2d15ed0b5f60.png)

​	现在已经可以在 Github 主页看到相关的 `tag`：	![Snipaste_2022-05-10_16-42-52](https://user-images.githubusercontent.com/94165481/167587491-1f5dfe1f-544a-4a14-9d7b-fe67a0a39aa1.png)

- 分支。在我们创建好 `main` 分支后，后续的开发都不会在 `main` 分支，一般会建立一个新的分支为 `develop` 。

  ```bash
  # 新建一个分支，但依然停留在当前分支
  $ git branch [branch-name]
  ```

  ![Snipaste_2022-05-10_16-49-52](https://user-images.githubusercontent.com/94165481/167588923-a03da65e-b708-4c6d-81cd-aafaec6a132a.png)

  已经创建一个名为 `develop` 的分支，但是当前还没有将本地的分支切换到 `develop`。

  ```bash
  # 切换到指定分支，并更新工作区
  $ git checkout [branch-name]
  ```

  ![Snipaste_2022-05-10_16-49-07](https://user-images.githubusercontent.com/94165481/167588758-329c5fe0-323e-40ae-a32c-d26076da1482.png)

- 推送分支到远程。

  ```bash
  # 推送本地分支到远程
  $ git push origin [branch-name]
  ```

  ![Snipaste_2022-05-10_16-55-44](https://user-images.githubusercontent.com/94165481/167590130-5385a8e4-0d38-4f16-8425-0527f0b0649a.png)

- 远程同步。在我们已经成功的创建远程分支之后，一段时间之后，我们需要先同步远程的代码到本地。

  ```bash
  # 下载远程仓库的所有变动
  $ git fetch [remote]
  
  # 取回远程仓库的变化，并与本地分支合并
  $ git pull [remote] [branch]
  ```

  - `$ git fetch [remote]` 是用来将远程的代码拉取到本地，但是不和本地的代码合并，而是放在暂存区。
  - `git pull [remote] [branch]` 是将远程的代码拉取到本地，并且将代码和本地的代码合并。

