# Git 使用说明文档

## 加入项目

  - 注册 Github 就不再赘述；

  - 加入一个项目需要通过项目拥有人的邀请，邀请邮件会发送到邮箱，通过邮箱链接接受邀请；
    ![InkedSnipaste_2022-05-10_14-52-37_LI](https://user-images.githubusercontent.com/105333498/167761998-b66e44a2-4ad7-454f-ad81-ca8bfaa733b4.jpg)

  - 加入成功后，我们就可以在自己的 Github 首页看到自己的 `Repositories`;

    ![Inked167567672-4a2ee196-3eb9-430d-8ae0-c2def12f8a63_LI](https://user-images.githubusercontent.com/105333498/167762192-fcf1d8ff-e7ef-413c-9d98-7612cb48d800.jpg)

## 开始之前

在开始使用 Git 之前，需要确保电脑已经安装了 Git，这里只讲 Windows 下的 Git 安装，MacOS已经系统自带 Git 了。

  - 下载 GIt，可以通过这个官方链接下载 [Git](https://git-scm.com/) ；
  - 下载后，安装默认点击`下一步`安装完成即可，具体的安装流程可以参考[这个](https://www.cnblogs.com/xueweisuoyong/p/11914045.html)；
  - `Windodws` 用户打开 `PowerShell`， `Mac` 用户打开 `终端` 操作 Git；
  - 在 Github 进入工程后，点击 `Code` ,可以看到 Git 的下载地址，这里有几个区别，`HTTPS` 的地址主要通过 Github 的邮箱和密码来验证权限；`SSH` 则通过一个在工程中加入的唯一的 SSH key 来验证权限。
  - 以通过账号密码来验证权限为例，拷贝 `HTTPS` 的 Git 地址：

  ![InkedSnipaste_2022-05-10_14-53-05_LI](https://user-images.githubusercontent.com/105333498/167762309-fb05d64a-d425-4b5a-8531-aac4ebf3ee54.jpg)

## Git 配置

安装完 Git 后就开始对 Git 进行配置操作，配置自己用户名和 Email，配置的命令如下：

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

## Git 原理

  在 Git中有四个概念：**「远程仓库、工作区、暂存区、版本库」**。远程仓库就是我们 Git 的服务器，用于存储已经管理团队的代码。

  工作区、暂存区、版本库是我们本地的，例如当我们初始化 `git init` 后，就会在当前的目录下出现 `.git` 目录，**「 GitTestProject 目录就是我们的工作区，而 .git 目录是我们的版本库所有的版  本信息都在这里」**。

  ![Snipaste_2022-05-11_14-24-47](https://user-images.githubusercontent.com/105333498/167782543-af07e66a-039e-4db5-b93a-e780f7563bb0.png)

  在 .git 目录下 index 文件(`.git/index`)，这就是 **「暂存区」**，叫做 `stage` 或者 `index` ，index 和我们的数据库的 index 类似，所以我们有时候也叫它为 **「索引」**。这四个区域实现的原理图所下所示：

  ![v2-2ba5b5e220c73820daadea21c9a1c4e5_720w](https://user-images.githubusercontent.com/105333498/167782767-6e40a32e-00b0-4b58-b86e-6f609a12fd67.jpg)
  
  从原理图中可以看出代码可以再不同的 level 之间转移，也可以跨 level 之间转移，所有的这些动作都是通过 Git 的命令去实现。
  初始化的时候 Git 还会自动为我们创建第一个分支 `main`，以及指向 main 的一个指针叫做 `HEAD`。

### 重点提示
    与 SVN 的不同是，Git 更多的操作是基于本地仓库。Git 的操作不再那么依赖于网络和远程仓库。那么，就意味着 Git 完全可以在本地提交版本、建立分支、合并分支甚至包括提交回滚等。也就是说所有的操作基本上都针对于本地仓库，而本地仓库和远程仓库之间的更多的关系基本上就是同步，拉取代码代码到本地 `Pull`/`Fetch` 和推送本次仓库到远程仓库 `Push` 等同步操作。所以，只有想让你的更新告诉别人或者想获取别人的更新的时候才需要更新远程仓库，其他时候你都可以在本地操作。这就是和 SVN 的最大的不同。**「每台电脑都是一份完整的仓库」**。

## 命令行操作

  ![bg2015120901](https://user-images.githubusercontent.com/94165481/167757863-13ee8f57-a7ce-4cc4-b67e-e033d3dbe88c.png)

### 克隆项目

 - **克隆项目**。在我们实际的工作环境中，都会从服务器上进行克隆项目到本地，Git 中使用 `git clone` 命令可以进行克隆项目：

   ```bash
   # 下载一个项目和它的整个代码历史
   $ git clone [url]
   ```

   ![Snipaste_2022-05-11_11-31-58](https://user-images.githubusercontent.com/105333498/167763698-945964f3-8fd3-4885-8afe-6d32abd99135.png)

   ![Snipaste_2022-05-11_11-32-48](https://user-images.githubusercontent.com/105333498/167763794-1e2b8f88-7979-4e8c-b983-1fd4f57ea91c.png)

   完成之后，文件夹中已经有相应的工程了，由于当前的工程只有默认的 `README.md` 的文件，我们可以来新建一个工程。

   ![Snipaste_2022-05-11_11-33-29](https://user-images.githubusercontent.com/105333498/167763859-20d2e670-7286-4306-9053-46689a7d551e.png)

   执行 `git clone` 就会生成一份副本，在本地仓库和工作区都会同步副本，具体的原理图如下所示：

    ![v2-2da2e4bdb966b3afa54d2a80a2341a8d_720w](https://user-images.githubusercontent.com/105333498/167783181-db9ecead-caf7-4eba-8905-9b747b971b2b.jpg)

### 提交代码

   从上面的图中我们可以到，代码可以在不同 level 之间移动，高 level 到低 level，或者逆向低 level 到高 level，也可以跨 level 之间移动。

   Git 中代码从低 level 到高 leve 的移动主要依靠以下命令：

   - `git add .`：全部修改或新增等有变化的文件添加进暂存区。
   - `git commit -m "提交信息"`：文件添加进本地仓库，`-m` 参数改为 `-am` 可以直接推向本地仓库。
   - `git push`：文件推向远程仓库。

   ![v2-7d454a2570bf96ad8f770a2975a4e532_720w](https://user-images.githubusercontent.com/105333498/167783836-9add1535-7d4c-4582-85de-961e2a723f67.jpg)

   运行`git commit -a`相当于运行 `git add` 把所有文件加入暂存区，然后再运行 `git commit` 把文件提交本地仓库。
   如果你不想添加全部文件到暂存区，可以参考下面到命令：
   ```bash
   # 添加指定文件到暂存区
   $ git add [file1] [file2] ...

   # 添加指定目录到暂存区，包括子目录
   $ git add [dir]

   # 添加当前目录的所有文件到暂存区
   $ git add .
   ```

具体操作如下：

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

    目前代码已经成功提交到了暂存区，也就是说现在只是提交到了我们本地，接下来，我们需要将这部分代码推送到远程服务器，这样其他的人也可以获取最新的代码。

  - **文件推向远程仓库**。

    ```bash
    # 上传本地指定分支到远程仓库
    $ git push [remote] [branch]
    ```
    
    ![Snipaste_2022-05-11_13-32-45](https://user-images.githubusercontent.com/105333498/167776131-93d65ede-7b28-4ad7-8b80-51b55f603a2c.png)


### 代码回退

  那么从高 level 向低 level 移动代码的命令如下：

  - `git pull`：从远程仓库拉取代码到本地。

  - `git reset --files`：用本地仓库覆盖暂存区中修改，也就是覆盖最后一次 `git add` 的内容。

  - `git checkout --files`：把文件从暂存区复制到工作区，用于放弃本地的修改。

  - `git checkout HEAD --files`：回退最后一次的提交内容。

    ![v2-52d2e66e643e3cf7feeb5fa7bed2f9fe_720w](https://user-images.githubusercontent.com/105333498/167784595-4be9562f-1a10-40ce-b1f4-ec120028a2a1.jpg)


具体操作如下：

  下面我用自己本地与 Github 的操作测试上面的命令，加深对上面的命令的理解和使用，当我在本地新建一个 Github 仓库中没有的文件：

  ![Snipaste_2022-05-11_14-49-05](https://user-images.githubusercontent.com/105333498/167786261-bae058fb-6fa9-4309-a08b-59fb32e5ee8a.png)


  ![Snipaste_2022-05-11_14-49-47](https://user-images.githubusercontent.com/105333498/167786401-023a66ec-d91b-4e81-b822-a553dc933874.png)

  可以看到文件的显示 `Untracked files：`未被追踪的文件，**「表示该文件未被git追踪管理」**。

  新添加的文件可以通过 **「git add 添加到在暂存区」**，**「这样文件就能够被 Git 进行追踪」**，此时再使用  `git status` 查看文件时，就可以看到两个文件已经是以 new file 的形式进行显示：

  ![Snipaste_2022-05-11_14-51-31](https://user-images.githubusercontent.com/105333498/167786750-b7197e51-b095-4142-ba8c-fa71ffcf16f2.png)

  - **从暂存区回退代码到工作区**

  ```bash
  # 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
  $ git reset [file]
  ```

  ![Snipaste_2022-05-11_14-55-03](https://user-images.githubusercontent.com/105333498/167787402-61dbcec5-9c13-4770-9589-10f6a1579d1a.png)

  可以看到暂存区的代码又回退到了工作区。也可以在使用命令：`git reset --hard HEAD^`，表示回退上一个版本，**「在Git中HEAD 表示当前版本，HEAD^ 表示上一个版本」**，若是有多个版本，这样表示就不方便了，可以使用`HEAD~10`，表示版本的次数。

  在 Git 每一个 commit 都会有自己的 commit 的 ID，可以通过 `git log` 进行查看。

  ![Snipaste_2022-05-11_14-59-30](https://user-images.githubusercontent.com/105333498/167788295-6c138abf-048b-4d7f-a48e-e0bf55689393.png)

  `commit`的本质就是：**「每次Git都会用暂存区的文件创建一个新的提交，把当前的分支指向新的提交节点，这样就完成了一次新的提交」**：

  ![v2-56bc64049856cd5746561aef85505d8d_720w](https://user-images.githubusercontent.com/105333498/167788596-f1873bbb-d356-4234-9f6e-b75090869b25.jpg)

  若是 `HEAD` 指针指向的是 `bran` 分支，那么新的节点就会成为 `jh509` 的子节点，并且形成新的分支：

  ![v2-98d8b69a3f602ed00405e6f8b60da061_720w](https://user-images.githubusercontent.com/105333498/167788678-ce84de38-cf95-44f6-aaa1-68804beccd51.jpg)

  也就可以使用 `git log --pretty=oneline`：直接输出commit的ID，信息比较简短，然后直接指定ID的回退：

  ```bash
  $ git reset --hard  5567a
  ```

  当你再次检查你的代码的时候就会回到了 id 为 5567a 版本，在 Git 的版本回退原理中，Git 的内部有一个指当当前版本的HEAD指针，只要从当前版本指回去就行了，所以 Git 版本的回退是特别快的，只需要移动指针，实现的原理图如下所示：

  ![v2-d56bdeb42747fbc15f4eeed864642e5b_b](https://user-images.githubusercontent.com/105333498/167788847-8df8ca86-a856-4cd3-9a33-76733b5f612f.jpg)


- **撤销修改**

  丢弃工作区的修改使用：

  ```bash
  # 恢复暂存区的指定文件到工作区
  $ git checkout [file]
  ```

  **这条命令中的 [file] 是不能漏的，若是只是 `git checkout` 就表示切换另一条分支的命令了。**

  在我的本地我直接修改：README.md 文件，然后使用 `git status` 进行查看，他表示文件处于 modified 状态：

  ![Snipaste_2022-05-11_15-06-57](https://user-images.githubusercontent.com/105333498/167789629-c31ad354-ea9a-4401-8a1a-8688849963e8.png)

  此时的 README.md 文件是还没有被添加进暂存区的，可以直接使用以下命令，撤销掉工作区的修改：

  ```bash
  git checkout -- README.md
  ```
- **提交回撤**
  
  1、**若是已经添加到暂存区了，就是用以下的命令进行回撤：**

    ```bash
    git reset HEAD README.md
    ```

    上面也演示了 `git reset` 命令，它既可以回退版本，又可以把暂存区的修改回退到工作区。当我们用 HEAD 时，表示最新的版本。

    当你提交了修改后，可以使用 `git diff` 查看两次提交之间的变动，它的本质就是 **「任意比较两个仓库之间的差异」**：

    ![v2-fe22f7502674dcefc2490811bac6cec6_720w](https://user-images.githubusercontent.com/105333498/167790115-43b3f7f2-d59d-4041-b20b-9d661012fdc3.jpg)
  
  2、**若是已经提交到远程仓库，就是用以下的命令回滚：**
  
     ```bash
     # 新建一个commit，用来撤销指定commit
     # 后者的所有变化都将被前者抵消，并且应用到当前分支
     $ git revert [commit]
     ```
   
   3、**`git reset` 和 `git revert` 的区别**
   
      - `git revert` 后会多出一条 commit，这里可进行回撤操作；

      - `git reset` 直接把之前 commit 删掉，非 git reset --hard 的操作是不会删掉修改代码，如果远程已经有之前代码，需要强推 `git push -f` ；

      - 如果想继续深究的，可以参考这篇[文章](https://juejin.cn/post/6844903614767448072)；



- **删除文件**

  在工作区直接使用 rm fileName，这个操作和 linux 的命令一样，若是文件已经提交版本库，从版本库中删除文件可以使用 `git rm` 命令进行删除，然后提交：

  ```text
  $ git rm README.md
  $ git commit -m "remove README.md"
  ```

  若是删除错了，可以使用 `git checkout -- README.md` 进行恢复，其原理就是使用版本库的文件替换工作区的文件。



### 代码冲突

  在团队中集体使用 Git 的时候，每个人都提交自己的代码最后合并到主干，总有会 push 失败的时候，因为 push 的本质：**「就是用你本地仓库的commit记录去覆盖远程仓库的commit记录」**。

  但是别人提交了一些代码，而你本地并没有这些代码，这样代码就会被覆盖，导致别人的 commit 的记录就不存在，这个是绝对不允许的。

  所以，每次 push 的时候 Git 就会检查，若是存在这种情况就是 push 失败，只要先 `git pull` 一下，将本地仓库与远程仓库先合并一下，最后 push 就可以成功了，若是文件中已经存在在冲突代码，只要打开文件重新解决一下冲突即可。
  
  因为解决冲突涉及内软较多，可以参考这篇[文章](https://www.liaoxuefeng.com/wiki/896043488029600/900004111093344) 。



### 分支管理

  *⭐️重点提示，为了统一文档内容和图片的描述，本文所有主分支 `main` 和图片中出现的 `main` 都是指同一个，我们都认为为 main 主分支。⭐️*

  Git 中比较最重要的一点就是分支的概念，有了分支就有了合并和衍合的操作，**「合并」**和**「衍合」**能够**「有效的对代码版本的管理」**。

  Git 的初始化中有一条默认的主分支叫做 `
  `，每一次的提交都会串成一条时间线，这就是一条分支，当前分支由 `HEAD `指针指向：

  ![v2-97435fd76d4f0e088418905c07ee57d5_b](https://user-images.githubusercontent.com/105333498/167790516-4f7f3f33-bbdd-496b-9f40-10ece044019b.gif)

  当每次发生代码提交的时候，当前指向就会向前形成一个新的版本，假如再创建一个新的分支 bran，并且当前的提交指向新的分支，这样新的分支随着时间的推移就会形成许多版本：

  ![v2-1fa112dd234bf38af795102b04cb8183_720w](https://user-images.githubusercontent.com/105333498/167790600-87adec0a-4983-4659-a2fd-0d8df7712fdb.jpg)

  当新分支开发完后，提交仓库，并合并到主干 main，最后删除 bran分支，这样就完成了一次个人的开发：

  ![v2-6dfa3b0db0406db580b9869dc6b5d294_720w](https://user-images.githubusercontent.com/105333498/167790724-cd1ff279-2efa-4d72-be5d-ba7f475a1997.jpg)

  所以，假如主分支上只建立一条分支的话，分支的合并是非常快速的，只需要移动 main 分支到当前提交，然后将 HEAD 指针指向 main，最后删除 bran 分支就完成了。

  但是，事实上并不是这样的，在一个多人协作的开发团队中，往往每个人都会建立自己的分支，有自己的提交，最后合并到主干，当自己提交的时候，远程仓库代码就会存在自己本地仓库并未有的代码，这样就会导致push失败。

  例如：程序员 A 和 B 同时迁出代码，他们的初始代码分支都如下图所示：

  ![v2-8da8eda06cf5af7f6d7a07ae47c10d5f_720w](https://user-images.githubusercontent.com/105333498/167791063-2b5c7d7d-4037-4f2f-b1c2-02b2efc383e3.jpg)

  当A开发自己的业务模块，提交代码并且合并到主干后，远程主干分支如下图所示：

  ![v2-56aded61773e239bf11f4326145a9f44_720w](https://user-images.githubusercontent.com/105333498/167791134-4fd5cad5-e3ab-4aaa-b335-fc39e0aa2475.jpg)

**「远程仓库 main 已经不再指向 gs234，而是新生成了一个版本 dfd453，作为当前指向的版本」**。

  与此同时，B 的本地也同时开发完自己的模块后，分支如下图所示：

  ![v2-9272ba481dfa50b453944cc7cabb5af1_720w](https://user-images.githubusercontent.com/105333498/167791210-9349a373-ef9a-4406-89d3-235e28c9b1c3.jpg)

  在 B 的本地环境中，他的 **「本地仓库 main 还是指向gs234」**，B 在自己新建立的一个分支`bran`中进行开发，开发完后合并分支，最后`main`就会指向`ed489`。

  当B再次提交代码，Git 就会检查远程仓库与 B 的本地仓库，进行对比后，发现远程仓库存在 B 的本地仓库不存在的代码，就需要 B 将远程仓库执行 `git pull`后，自行解决冲突。

  上面说了分支基本原理，已经管理分支出现的问题，下面我们就来一步一步的深入操作分支的基本命令。



具体操作如下：

- **新建分支**。

    Git 新建一个分支的命令为：`git branch <分支名字>`，新建立后分之后，切换分支的命令为：`git checkout <分支名字>`。

    新建分支的实质：**「就是新建立一个引用，指向当前提交，main 就好比一个引用」**；切换分支的实质：就是将`HEAD`由指向原来的引用，重新指向要切换的分支的引用上：

    ![v2-a76627a106ee2a4faa15354dc9762036_720w](https://user-images.githubusercontent.com/105333498/167792259-364e6c67-c891-4b7c-a748-2bf94f668b5a.jpg)

    当然上面创建分支并且合并分支的两条命令可以合并成一条命令：`git checkout -b <分支名字>`

    当切换分之后，每次 commit 提交代码时 HEAD 指针就会跟随着新的 bran 分支移动，形成 bran 分支上的每一个版本：

    ![v2-96999b450c9b98d1756a00d8052cc667_720w](https://user-images.githubusercontent.com/105333498/167792200-6a89e803-03c3-4500-92fb-56b79e821dd5.jpg)

    假如，在新的bran分支上开发到某一个版本，再次切换回 main 分支进行开发就会形成分叉：

    ![v2-1c5331fb5b9d4e4d3a6a2aaf3b2622b1_720w](https://user-images.githubusercontent.com/105333498/167792430-80261ac0-61f5-45e9-8da6-6494ca9f6eea.jpg)


    ```bash
    # 新建一个分支，但依然停留在当前分支
    $ git branch [branch-name]
    ```

    ![Snipaste_2022-05-11_13-48-37](https://user-images.githubusercontent.com/105333498/167777623-643e9ea3-53ce-4279-ba11-d807262656a3.png)

    创建一个名为 `develop` 的分支，但是当前还没有将本地的分支切换到 `develop`。

    ```bash
    # 切换到指定分支，并更新工作区
    $ git checkout [branch-name]
    ```

    ![Snipaste_2022-05-11_13-49-24](https://user-images.githubusercontent.com/105333498/167777714-e3ebe7dd-3108-447e-beaf-a25a81ad629e.png)


- **查看分支**。

    当分支创建好了，你可以通过：`git branch`，来查看自己本地的分支情况。在提交 Git 变化到远程服务器之前，我们来查看有远程有哪些分支：

    ```bash
    # 列出所有本地分支
    $ git branch
    # 列出所有远程分支
    $ git branch -r
    # 列出所有本地分支和远程分支
    $ git branch -a
    ```

    ![Snipaste_2022-05-11_11-38-13](https://user-images.githubusercontent.com/105333498/167764336-bb2e1078-ae23-4335-9feb-c90a636f4942.png)
    可以看到，分支前面带有`*`号的表示当前的分支。远程分支目前有`main` 分支，这一般为主分支，。我们当前是新建项目，那么就会推送到主分支。

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


- **删除分支**。合并完成后的分支，当不再需要的时候，可以删除分支。

    ```bash
    # 删除一个分支
    $ git branch [branch-name]
    ```

- **拉取分支**。

    ```bash
    # 下载远程仓库的所有变动
    $ git fetch [remote]
    # 取回远程仓库的变化，并与本地分支合并
    $ git pull [remote] [branch]
    ```

### 标签管理
  Git中使用的标签有两种类型：「轻量级的（lightweight）和含附注的（annotated）」。轻量级标签只需在 git tag 后加上标签的名字，就可以添加标签。
  标签管理作为开发人员可能很少使用，可以作为了解，「tag是针对Git中某一时间某一版本打上标签」，tag 的使用命令也是非常的简单。

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

    ![Snipaste_2022-05-11_14-16-29](https://user-images.githubusercontent.com/105333498/167781466-bcd73af1-85da-4856-b75f-be94875126f2.png)

     现在已经可以在 Github 主页看到相关的 `tag`：

    ![Snipaste_2022-05-11_14-17-43](https://user-images.githubusercontent.com/105333498/167781560-201b3205-2a97-4ed5-85c6-b8159f25ae98.png)

 - **删除标签**

    删除标签若是标签没有推向远程仓库，直接使用以下命令删除：

    ```bash
    $ git tag -d [tag]
    ```

    若是标签已经推向远程仓库，先删除本地，再删除远程仓库的标签：

    ```bash
    $ git tag -d [tag]
    $ git push origin :refs/tags/[tag]
    ```

- **查看标签**

    git tag的方式是查看所有的标签，git show <标签名>的方式是查看每个特定的标签

    ```text
    $ git tag
    $ git show [tag]
    ```

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



参考内容：

- [图解Git操作，一篇就够 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/263050507)
- [常用 Git 命令清单 - 阮一峰的网络日志 (ruanyifeng.com)](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

