# L07 Exercise 01 Creating and Editing a New File with Vim - Walkthrough
---

本节为 L06 的讲解课（walkthrough）。



要求：必须动手练习。



`:q!` 中的 `!` 表示放弃更改。



> **Git 命令 DIY**
>
> 提交 git 的版本通常很固定：`git add *; git commit -m 'some comments'; git push`，虽然 Windows Terminal 中可以配置 PowerShell 的历史命令，但总要切到中间修改注释信息，时间一长感觉不太高效。如果有个自定义命令，把提交注释放到最后，就会方便很多：
>
> ```shell
> $ git diyCmd 'some comment'
> ```
>
> 于是尝试用 git 别名：（`acp` 即 `add`、`commit`、`push` 的缩写）
>
> ```shell
> $ git config --global alias.acp '!git add * && git commit -m \"$1\" && git push'
> ```
>
> 但这样配置后，前两个命令能正常运行，但 `git push` 始终会把我的注释内容理解成要推送的目标分支。为了让 `git push` 忽略最后的注释，再尝试：
>
> ```shell
> $ git config --global alias.acp '!git add * && git commit -m \"$1\" && git push # '
> ```
>
> 就是说，让后面的参数在执行时变成一段 `shell` 脚本注释。经测试，果然能行。以后类似的情况都能应对了。
>
> 其实这个别名的第一版是问的 ChatGPT，但 `git push` 报错后，ChatGPT 分析原因为“Git 不支持在别名中直接传递参数”，建议我通过 `.bat` 批处理任务实现。试了几次，好歹调通了：
>
> ```bat
> # file path: {GIT_HOME}\cmd\git-acp.bat
> @echo off
> git add *
> git commit -m %1
> git push
> ```
>
> 但这样写效率很低：又要创建文件，又要配置环境变量，运行的格式还必须是 `git-acp 'some comment'`，后面要修改命令更麻烦，没法使用 git 的内置命令。这样写还不如写成 PowerShell 的脚本：
>
> ```shell
> # git-acp.ps1
> param(
>     [string]$Comment = ""
> )
> cd "$(pwd)"
> git add *
> git commit -m "diy commit: $Comment"
> git push
> ```
>
> 感觉越来越跑偏了……本来加个 `<空格>#<空格>` 就解决的，被 ChatGPT 这么一带就搞错大方向了。可见提高效率的关键还是在于自己的思考和积累。
