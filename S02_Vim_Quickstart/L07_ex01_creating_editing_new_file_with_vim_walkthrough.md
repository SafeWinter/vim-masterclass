# L07 Exercise 01 Creating and Editing a New File with Vim - Walkthrough
---

本节为 L06 的讲解课。



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
> 但这样配置后，前两个命令能正常运行，但 `git push` 始终会把我的注释内容理解成要推送的目标分支。
