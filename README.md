# BUAASE2025-团队项目-版本控制

> “Your organization’s codebase is sustainable when you are able to change all of the things that you ought to change, safely, and can do so for the life of your codebase.”
>
> ——[Software Engineering at Google](https://abseil.io/resources/swe-book/html/toc.html), Titus Winters, Tom Manshreck and Hyrum Wright

课程的团队课设最终要求大家交付一个完整可用的**软件系统**。时长两个月的团队开发中，我们将时时对团队**最重要的资产**——**代码库**进行修改、迭代和完善。因此，保障它**稳定、安全、可持续地存在**，并能够**稳健地持续合并来自每个成员的变更、扩展和迭代**是重要的。

我们可以采用无数种可能方式来管理这一资产：基于群文件分享代码压缩包会得到助教组充满敬意的赞👍、邮寄代码的完整纸质副本会在这门课程的历史上留下足够先锋的脚印👣......但如果你也一样，对 `软工课堂展示-Pre-Draft5By熊-ffffffinal最终版真的绝对不再改了.pptx` 这样的文件名抱持与生俱来的恐惧、又或是憧憬无纸化办公的环保主义者，那么在团队开发中引入版本控制系统（Version Control System, VCS），绝对是值得的投资——事实上，也是当下软件工程领域明确的共识。

> **软件工程是随着时间的推移而集成的编程......开发本质上是一个分支和合并的过程，无论是在多个开发人员之间还是在不同时间点的单个开发人员之间进行协调。**

多人、长时的开发流程，需要正式的版本控制系统来管理源代码、协调工程师之间的活动。团队开发的过程中我们会自然地产生如下需要：

- 追踪工作的最新进度和历史进展；
- 并行地进行工作，提交更改；
- 合并修改、跟踪合并；
- ......

为了支撑这些需要，除了将 VCS 集成进我们的工作流程之外，我们还需有一套共识性的规范来指导对 VCS 的使用——团队开发中对代码库负责的不是**某一个人**，而是**每一个人**。

在这篇 Guide 里我们将一起通过一次团队的实践，认识版本控制系统在集体开发中的具体做法，并对形成行之有效的协作规范有所见解。

版本控制系统的选择有很多，你可在[这里](https://zh.wikipedia.org/wiki/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)进一步了解。这篇 Guide 基于目前最流行、也是大家最可能选用的分布式版本控制系统 Git 设计。

## 需要做什么？

**附录 A** 提供了一个软件工程小组的 Git 规范。接下来会给定一些任务，请依据指引遵照这份规范来进行代码修改和 Git 操作。

请注意，这份 Git 规范并不是团队开发的**最佳实践**，在不同的情形下、不同的团队中需要针对各类因素来设计适用的规范和工作流。我们基于这样一个目标采用了这份规范并设计了这次作业：涵盖团队开发阶段使用版本控制系统时可能遇到的常见场景和具体问题，从而让大家对这些问题有基本的认识、进而制定和协调最适用于各自团队的工作流。

**助教组会根据 commit 记录等仓库遗留的操作记录检查每个团队的完成情况。**

请保留全部的操作记录，包括分支、issue、pr 等。

当你的操作出现不致命的小差错、与“规范”相悖时，不用担心，这些无心之过可以原样保留在操作历史里。但是，“觉得自己搞砸了”的情形下，希望你能在代码仓库根目录下的 `error-logs.txt` 中留下你对错误的记录。

如果出现团队成员误操作、导致难以还原的情况，请首先了解可能的恢复方式、或在课程群中讨论有关做法，在完全无果的情况下可以重新开始。再次提醒大家：团队开发中对代码库负责的不是**某一个人**，而是**每一个人**，请<u>**谨慎地对待这份团队最重要的资产**</u>。这些情况，需要在作业提交时记录。

助教组可能会根据记录情况询问团队相关问题。

## 任务列表

请按照顺序完成各组任务。同组内无序列表标注的任务没有严格的顺序。

标记为 `🚧Maintenance` 的任务请团队中的**特定成员**负责，通常可以由小组中的 DevOps 岗完成——当然，也可以分配工作给某几位同学一起完成；

标记为 `🧑‍💻Every` 的任务请团队中的**每一位成员**参与；

标记为 `🚩Team` 的任务请团队将列表中的任务分配给各位成员完成，**每位成员至少完成一项、一个任务只能分配给一个人完成**。

### PRE. 团队的准备

#### `🧑‍💻Every` 团队协作的事前讨论

1. 请大家在一起讨论对于 DevOps 的理解，分配本团队的 DevOps 相关工作。操作上，也可以由团队决定一位同学来担当全部相关工作。
2. 请大家调研并根据小组内的网络环境、使用习惯等因素决定 DevOps 的各项考虑和服务选型，也可以使用一体化的 DevOps 平台例如[腾讯云 CODING](https://coding.net/). 至少，需要决定一款代码托管平台。**对于这次作业**，请在 [GitHub](https://github.com/) 或 [GitCode](https://gitcode.com/) 中二选一完成。 
3. 选择好之后，请各位成员在相关平台上完成账户注册、创建组织等工作。请注意，本次作业的代码仓库需要保证**至少课程组内部可以自由访问**以保证公正性；除非特殊情况，建议保持公开。

#### `🚧Maintenance` 初始化代码仓库

1. `Fork`（或在使用其他平台时 `Clone`）[GitHub 仓库](https://github.com/kuma-xx/BUAASE2025-TeamVersionControl) 或 [GitCode 仓库](https://gitcode.com/CodingNoBorder/BUAASE2025-TeamVersionControl)，初始化本团队的仓库；
2. 设置代码仓库中成员的相关权限；
3. 建立一个 `dev` 分支；
4. 检出分支 `chore/init`；
5. 在根目录下创建一个 `.gitignore` 文件，忽略根目录下的 `info.txt` 文件；
6. 在根目录下创建一个 `error-logs.txt` 文件；
7. 为仓库设置 Issue 模板，你可以参照 [GitHub 教程](https://docs.github.com/zh/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)，或 [GitCode 教程](https://docs.gitcode.com/docs/help/home/org_project/issue/issue_template)；
8. 提交更改，按照合并规范操作，最终合并你的更改到 `dev` 分支；
9. 通知团队的所有成员现在可以开始进入下一个阶段 `Task.1` 了。

### Task.1 

#### `🧑‍💻Every` 自我介绍！

1. 每位成员：拉取代码仓库到本地；

2. 在根目录下新建一个 `info.txt` 文件，向其中添加如下信息：

   ```
   name: <你的用户名>
   description: <你的一句话自我介绍>
   ```

   请注意不要包含太敏感的个人信息。

#### `🚩Team` 各写各的！

1. 接下来的任务，模拟开发中的各种情形，所有操作在 `/src` 下完成。提醒：**请注意分支和提交规范**。

2. 请认领如下任务中的至少一项：

   - 新建文件 `frontend.json`，格式如下：

     ```json
     {
         "data": [
             {
                 "name": "<名称>",
                 "link": "<链接>"
             },
                 ...
         ]
     }
     ```

     列举至少三个你所了解的前端框架。

   - 新建文件 `backend.json`，格式如下：

     ```json
     {
         "data": [
             {
                 "name": "<名称>",
                 "link": "<链接>"
             },
             	...
         ]
     }
     ```

     列举至少三个你所了解的后端框架。

   - 新建文件 `midend.json`，格式如下：

     ```json
     {
         "data": [
             {
                 "content": "<内容>",
                 "language": "<语言>"
             },
             	...
         ]
     }
     ```

     列举至少两条你所了解的双关 / 谐音冷笑话。

   - 修改文件 `ave-mujica.json`，文件内记录了乐队 Ave Mujica 的[成员列表](https://zh.moegirl.org.cn/Ave_Mujica)，其中有一项似乎记载错误。**这是一个 BUG**，请按照 `Bug 提出与修复` 的规范进行修复。如果成员描述和你的喜好不一致，你也可以声称某一项是 **Bug** 并修改为你喜欢的。错误的项也许没那么错也说不定——

   - 修改文件 `livehouse-around.json`，文件内记录了附近的几处演出场所的位置（所在的区）和名字，其中有一项位置似乎记载错误。**这是一个 BUG**，请按照 `Bug 提出与修复` 的规范进行修复。如果演出场所的位置和你的喜好不一致，你也可以声称某一项是 **Bug** 并修改为你喜欢的。课余时间多看演出、享受现场音乐吧——

   - 修改文件 `band-list.json`，文件内记录了一些数据。原本的记录方法是：

     ```json
     {
         "data": [
             {
                 "name": "<名字>",
                 "en-name": "<英文名字>"
             },
             	...
         ]
     }
     ```

     助教派来的 PM 路过瞅了一眼，拍了拍脑袋，觉得太长了，需要**重构**成如下形式：

     ```json
     {
         "data": {
             "names": ["<所有名字>"],
             "en-names": ["<所有英文名字>"]
         }
     }
     ```

     请你不跟 ta 一般见识，帮 ta 完成这个微不足道的梦想。小心二次元——

   - 修改文件 `really-ugly-json.json`，代码风格差强人意，请你帮忙**调整代码风格（不影响语义）**。请写美丽的代码——

3. 当你完成任务后，提交更改（aka. `git commit`）；

4. 按照合并规范操作到提出 Pull Request；

5. 全员完成后进行到下一阶段。

#### `🧑‍💻Every` 第一次合并！

1. 请大家在一起讨论你们如何进行 Code Review、如何处理团队产生的 Pull Request；
2. 请大家完成本次任务中所有产生的合并，如果产生了冲突请讨论为什么会产生冲突、应该如何解决。并且讨论附录 A 中的合并规范可能出于什么原因要求采用 `git rebase`，而没有提到我们更为熟悉也一如其名的 `git merge`，这样的选择会带来什么样的问题和益处？可以参考[这篇文章](https://blog.csdn.net/kevinxxw/article/details/123980372/)来了解相关信息；
3. 请大家根据**分支规范**完成**发布前的确认**、**版本发布**和**Tag 操作**。然后，请根据你们的实践结果在一起讨论完成一次迭代后，你们如何完成代码的确认和发布。

### Task.2

#### `🚩Team` 各写各的！

1. 接下来的任务，所有操作均在 `/src/info` 下完成，其中预置文件的格式均相同：

   ```json
   {
       "username": "<用户名>",
       "data": "<数据>"
   }
   ```

   请保留格式，只修改内容;

2. 请认领如下任务中的至少一项，每位同学领取的任务不能相同，**先不要着急完成**：

   - 修改文件 `character.json`，将内容修改为你的用户名和你最喜欢的游戏角色，如果你不当二次元的话请你填写你最喜欢的字母；
   - 修改文件 `elevator.json`，将内容修改为你的用户名和你最讨厌的电梯。大运村真恐怖啊——；
   - 修改文件 `emoji.json`，将内容修改为你的用户名和你最喜欢的 emoji；
   - 修改文件 `json.json`，将内容修改为你的用户名和你最喜欢的 json 文件内容；
   - 修改文件 `model.json`，将内容修改为你的用户名和你最喜欢的大语言模型；
   - 修改文件 `note.json`，将内容修改为你的用户名和你最喜欢的名人名言，或者你最喜欢的钞票面值；
   - 修改文件 `software.json`，将内容修改为你的用户名和你每天使用最久的软件。

3. 认领好任务后，请**在此时一次检出新分支，对应你选择的一项**，命名为 `feature/type-1`，`type` 对应你选择的那项任务，例如 `feature/emoji-1`；

4. **仍然不要开始完成任务**，回到第二步，认领你**第一次没有选择**的一项，每位同学领取的任务不能相同。然后**再次进行第三步**，这次将分支命名为 `feature/type-2`；

5. 现在可以开始完成**你所选择的第一项任务了**。请在 `feature/type-1` 分支上操作，完成修改之后，**提交一次更改（FYI, aka. `git commit`）**；然后再次修改 `<数据>` 项的内容为其他内容，**再次提交一次更改**。接下来，执行合并规范至**提交 Pull Request**。**等待，不要开始第二项任务**；

#### `🚧Maintenance` 第一项任务，完成！

1. 请按照你们团队的 Code Review 和 Pull Request 处理流程，由有仓库管理权限的成员完成第一项任务所做修改的所有合并工作；
2. 解决掉所有 Pull Request 后，请仓库管理者通知大家可以进行第二项任务了。

#### `🚩Team` 各写各的！

1. 请完成你所选择的第二项任务。请切换到 `feature/type-2` 分支，完成修改之后，提交更改，然后再执行合并规范，**如果此时你遇到了冲突，请解决每一个冲突**：如果有来自他人编辑的信息，**出于尊重请你把信息合并成**：

   ```json
   {
       "username": "<他人的用户名>, <你的用户名>",
       "data": "<他人的最新数据>, <你的数据>"
   }
   ```

   的形式；

2. 按照合并规范操作到提出 Pull Request，然后**不用再等待**，**请团队的代码管理成员 `🚧Maintenance` 尽快处理 Pull Request**，使修改合并到 `dev` 分支。

#### `🧑‍💻Every` 第二项任务，完成！

1. 请大家在一起检查最终完成的 `dev` 分支代码，是否出现了修改丢失的状况。如果有，是谁的什么操作导致的？
2. 请讨论在哪些地方遇到了冲突，如何解决，有没有意料之外的状况，应对这些状况进行了哪些操作。如果在合并 Pull Request 的阶段遇到了冲突，请讨论冲突的缘由。作为参考，可以在完成后的代码仓库下执行命令 `gitk`，对照显示的分支图进行讨论；
3. 请大家根据**分支规范**完成**发布前的确认**、**版本发布**和**Tag 操作**，发布第二次迭代后完成的版本。

### Task. HotFix!

#### `🧑‍💻Every` 超烫手的修复！

1. 请大家一起完成以下任务，或许只需要一个人来操作，但需要所有人了解操作的流程。

2. 请设想这样一个场景：在发布前检查中你们发现 `/src/tofix/classdata.json ` 存在 **Bug**：由于助教的某种疏忽，任课老师的名字打错了！请依照**分支规范**的说明，在 `release` 分支上进行修复；

3. 请设想这样一个场景：在将代码开源之前，你们突然发现 `/src/tofix/SUPER-SENSITIVE-DATA.txt` 含有某种绝密信息！而该文件（和它的信息）已经出现在远端仓库（的许多许多次提交）中了。**请先 Clone 一份你们的仓库来避免惨剧发生**，然后根据[这篇指引](https://docs.github.com/zh/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository)执行操作，将这个文件从所有提交中移除，然后**在远端新建一个代码库**，将你们完成操作的结果推送到**新的代码库**。务请注意：**这个文件是在你们开始修改前被不怀好意的助教引入的，请检查仓库中你们开始本次作业以前的各次提交，查找文件在被移动到这个位置之前还在哪里出现过，对应又该如何执行操作。**

   > 找不到也没关系啦！但请一定要注意清除敏感数据时要考虑到文件或许被移动或改名而存在于其他路径的状况。

### Task. Conclusion

#### `🧑‍💻Every` 写字！

1. 作为作业的终点，请在团队博客上提交一篇博客，内容至少包括：

   - 团队的代码仓库地址；
   - 团队完成 **Task. HotFix!** 后新建的代码仓库地址；
   - 你们代码仓库的分支图示，方法有很多。当然也可以在完成后的代码仓库下执行命令 gitk 获得，tips: 当你安装 Git 时应该已经安装了 gitk 工具；但如果你们使用 macOS，且使用 homebrew 安装了 Git，可以执行命令 `brew install git-gui` 获取相关软件包；
   - 需要说明的状况。

2. 同时，推荐团队完成以下内容，这部分内容在之后的团队项目博客作业（具体来说是项目展示部分）中仍然需要完成，因此现在完成可以减少之后的负担：

   - 团队选定的 DevOps 技术选型以及选择的原因、使用相关技术的方式；团队对代码仓库的管理、对这方面工作的安排；
   - 团队对于代码审查的考虑，代码发布的流程；
   - 在代码管理中，团队会遇到哪些风险，如何解决这些风险；

3. 最后，如果确实有所心得，希望团队能记载过程中种种实践和讨论的所得，梳理一下，这些心得可能包括：

   - 这次实践中遇到了哪些问题，如何解决和避免；
   - 版本管理系统的协作中，除了使用软件之外，还需考虑哪些内容：例如，流程、规范等；
   - 适用于你们团队的版本管理系统协作规范；
   - 对具体软件操作的理解：例如上面提及的 `git merge `和 `git rebase`；

   等等，这些内容不一定要留在博客中，更不参与计分，但一定会成为团队实践和个人软工路上的宝贵财富。

## 附录 A

一个软件工程小组的 Git 规范。

> 这份规范由 [roife](https://github.com/roife) 在 2022 级北航软件工程的团队开发中编写。


### ⚙ 提交规范

#### Commit Message

```jsx
<type>(<scope>): <subject>

<body>
```

- type 有下面几类
  - `feat` 新功能
  - `fix` 修补bug（在 `<body>` 里面加对应的 Issue ID）
  - `test` 测试相关
  - `style` 代码风格变化（不影响运行）
  - `refactor` 重构（没有新增功能或修复 BUG）
  - `perf` 性能优化
  - `chore` 构建过程变动（包括构建工具/CI等）
- scope（可选）：影响的模块
- subject：主题（一句话简要描述）
- body（可选）：详细描述，包括相关的 issue、bug 以及具体变动等，可以有多行

#### 例子

```bash
[feat](账号模块): 增加微信登录验证
```
```bash
[fix](管理员 UI): Safari 下界面适配

1. xxx 元素 yyyy
2. aaa 页面 bbbb

Issue: #3
```
```bash
[refactor](招聘信息接口): xxx 接口更新
```
```bash
[style]: 格式规范更改，重新格式化
```

**请不要用 `fix #3` 之类的 message 关闭 Issue！请按照 BUG 提出与修复的描述用 Pull Request！**

### 🎋 分支规范

代码仓库分为以下六类分支：

1. main 分支 `线上在跑的版本`
    1. 提供给用户使用的**正式版本**和**稳定版本**；
    2. 🏷️ 所有**版本发布**和 **Tag** 操作都在这里进行；
    3. ❌ **不允许**开发者日常 push，只允许从 release 合并。
2. release 分支 `将要上线的版本`
    1. 从 develop 分支检出，只用于发布前的确认；
    2. 允许从中分出 fix 分支，修复的 commit 需要 push 回 dev；
    3. ❌ **不允许**开发者日常 push，只允许从 dev 合并。
3. dev 分支 `日常开发汇总`
    1. 开发者可以检出 feature 和 fix 分支，开发完成后 push 回 dev；
    2. 保证领先于 main；
    3. ❌ **不允许**开发者日常 push，只允许完成功能开发或 bug 修复后通过 pull request 进行合并。
4. feature 分支
    1. 从 dev 分支检出，用于新功能开发；
    2. 命名为 `feature/name`，如 `feature/resume_generation`；
    3. 开发完毕，经过测试后合并到 dev 分支；
    4. ✅ 允许开发者日常 push.
5. fix 分支
    1. 从 dev 或 release 分支检出，用于 bug 修复（feature 过程中的 bug 直接就地解决）；
    2. **特殊情况下**允许直接从 main 直接开 fix 分支进行修复；
    3. 命名为 `fix/issue_id`，如 `fix/2` ;
    4. 修复完毕，经过测试后合并到原来的分支（dev/release/main），**并且保证同时合并到 dev**;
    5. ✅ 允许开发者日常 push.
6. chore 分支
    1. 从 dev 分支检出，用于各项修正，如重构、风格优化等；
    2. 命名为 `chore/name`，如 `chore/resume_generation`；
    3. 开发完毕，经过测试后合并到 dev 分支；
    4. ✅ 允许开发者日常 push.


### 🧬 分支合并

<u>**不许在别人的分支上开新分支，只能在主分支开分支。分支粒度可以尽可能小。**</u>

#### 合并到 `dev` 分支

我在 `my_feature` 上开发了一段时间了，想要合并到 `dev`，可以这么做：

1. 拉取最新的 `dev` ；
2. `rebase` 当前分支到 `dev`，并且解决 `rebase` 带来的问题；
3. `rebase` 完成后，将当前分支推到远端（**TA注：请考虑一下这个推送的操作要在什么条件下进行**），在 GitHub 上发起一个到 dev 的 Pull Request，**及时合并**，防止更多冲突。

#### 想解决 `dev` 上和我有冲突的新提交，但是不想合并到 `dev`

假设我在 `my_feature` 上开发，其他人开发的功能上线到 `dev` 分支了。

**那么我可以在当前的分支下 `rebase` 一下 `dev` 分支**，这样我这个分支的几个 commits 相对于 `main` 还是处于最顶端的，也就是说 `rebase` 主要用来跟上游同步，同时把自己的修改顶到最上面。

开发的时候，如果你的功能很复杂，**尽量及时 `rebase` 上游分支**，有冲突提前就 fix 掉。

> 这样即使我们自己的分支开发了很久，也不会积累太多的 conflict，最后合并进主分支的时候特别轻松。
>
> 反对从主分支 checkout 出新分支，自己闷头开发，结果最后合并进主分支的时候，产生有一大堆冲突。

最后，<u>**不要在公共分支（例如 dev/main）上瞎 rebase！**</u>

### 🪳 BUG 提出与修复

1. 提出一个 issue，按照 template **简要记录** bug 相关的信息，事后能看懂即可，不用太详细；
2. 开一个 `fix` 分支，对 bug 进行修复。fix 修复完成后需要**进行测试，确认已经修复**；
3. 开一个 pull request，并将 pull request 和 issue 关联起来；
4. 合并 PR。

❌ **不要在 commit message 里面用 `fix #3` 等直接 close issue，应该在 pull request 关联 issue**.

如果是在 feature 分支**开发过程**中遇到的小 bug，可以直接顺手本地修了，不用按照这个流程来。

## 附录 B

### Git 的基本操作

我们预设大家已经通过既往课程对 VCS 有了基本的认识、并熟悉个人代码管理的基本操作。如果你不具备相关的背景知识，这里提供如下链接供你参考：

- [廖雪峰的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [Pro Git](https://git-scm.com/book/zh/v2)

### 参考

这篇 Guide 参考了 [Git 团队协作](https://www.oreilly.com/library/view/git-for-teams/9781491911204/) 和 [Google 软件工程](https://abseil.io/resources/swe-book/html/toc.html)。对于前者，请寻找出版商购买；对于后者，你可以线上阅读[中文版](https://qiangmzsx.github.io/Software-Engineering-at-Google/)或[英文版](https://abseil.io/resources/swe-book/html/toc.html)。

这里还有一些参考文章以备阅读：

- [Git 使用 Merge 和 Rebase](https://blog.csdn.net/kevinxxw/article/details/123980372/)
- [Commit message 和 Change log 编写指南](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)
- [GitHub Pull Request入门](https://zhuanlan.zhihu.com/p/51199833)
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)

### 实用工具

- [Git 分支演示](https://learngitbranching.js.org/?NODEMO=&locale=zh_CN)

> Ver.5 by @KumaXX with KkKk, Toby, volca, Yt