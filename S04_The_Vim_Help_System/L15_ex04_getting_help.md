# L15 Exercise 04 - Getting Help
---



## 1 训练目标

熟悉 `Vim` 帮助系统的用法。[^1]



## 2 操作指令

### 2.1 打开文件 help.txt

打开一个本地命令行会话，使用 `Vim` 打开文件 `help.txt`（练习文件默认解压到 `Downloads` 文件夹下）：

```shell
cd Downloads
cd vimclass
vim help.txt
```



### 2.2 打开帮助系统

输入：`:help` + <kbd>Enter</kbd> 打开帮助进行浏览。须知帮助文档也是一个普通的文本文件。



### 2.3 退出帮助系统

使用 `:q` + <kbd>Enter</kbd>



### 2.4 再次打开帮助系统

换用 `:h` + <kbd>Enter</kbd> 再次打开 Vim 帮助。很多时候，Vim 命令都有缩写形式。这里的 `:h` 相当于 `:help`。



#### 2.4.1 用学过的命令浏览帮助文档

前面已经学了一些 `Vim` 命令。使用帮助系统获取下列命令的帮助文档。仔细阅读文档加深对每一个命令的印象：

- `:h i` 
- `:h :wq` 
- `:h :q` 
- `:h Ctrl-f`：可使用 `[count]Ctrl-f` 下翻 `count` 页，或 `[count]Ctrl-b` 上翻 `count` 页
- `:h ^f` （注意：快捷键 `^` 相当于 `Ctrl`，因此 `^f` 与 `Ctrl-f` 是同一个意思）
- `:h ^b` 
- `:h w`：文档中的 `<S-Right>` 表示按住 <kbd>Shift</kbd> 的同时再按下右箭头 <kbd>Right</kbd> 键。



#### 2.4.2 练习在帮助文档间跳转

键入 `:h w` + <kbd>Enter</kbd> 查看 <kbd>W</kbd> 命令的帮助文档。将光标定位到单词 `exclusive` 上，按 <kbd>Ctrl</kbd> + <kbd>]</kbd> 跳转到 `exclusive` 对应的帮助页；查阅完毕，使用 <kbd>Ctrl</kbd> + <kbd>O</kbd> 返回上一个帮助页（即 <kbd>W</kbd> 命令。这里的 “O” 表示 “Old”，有 “过去的、旧的” 的意思）。

再将光标定位到单词 `count` 上，按 <kbd>Ctrl</kbd> + <kbd>]</kbd> 查看该主题（subject）的帮助文档。阅读完 `count` 相关帮助后，按 <kbd>Ctrl</kbd> + <kbd>O</kbd> 返回 上一个帮助主题。



#### 2.4.3 练习使用 Ctrl-g 的等效命令

要查看 <kbd>Ctrl</kbd> + <kbd>G</kbd> 的帮助文档，输入 `:h ^g` + <kbd>Enter</kbd>。还有和它类似的命令吗？不错，还有 `:f` 或 `:file` 命令。输入 `:f` + <kbd>Enter</kbd> 即可查看帮助。留意屏幕下方出现的一行文本。它将显示当面在用的帮助文档的名称。 注意屏幕下方出现的一行文本。 它会显示当前帮助文件的具体路径。



#### 2.4.4 回到之前编辑的文件

按下 <kbd>Ctrl</kbd> + <kbd>WW</kbd>（即按住 <kbd>Ctrl</kbd> 并敲两次 <kbd>W</kbd>），此时光标位于位于底部那个窗口，即练习刚开始时打开的 `help.txt` 文件所在的窗口。可通过 <kbd>Ctrl</kbd> + <kbd>G</kbd>、或者使用 `:f` 或 `:file` 命令进一步确认。



### 2.5 亲自动手

按下 <kbd>Ctrl</kbd> + <kbd>WW</kbd> 让光标再次回到 `Vim` 帮助窗口。回忆几个已经学过的命令，然后通过帮助系统查看其文档。用本节学到的知识尽情探索吧。



### 2.6 结束练习

完成练习，输入 `:q` + <kbd>Enter</kbd> 退出帮助系统；使用 `:q!` + <kbd>Enter</kbd> 停止文件编辑并退出 `Vim`。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-04-GettingHelp.pdf`

