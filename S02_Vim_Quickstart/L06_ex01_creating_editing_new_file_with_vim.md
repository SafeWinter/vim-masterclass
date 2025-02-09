# L06 Exercise 01 Creating and Editing a New File with Vim
---



## 1 训练目标

- 练习用 `Vim` 创建文件、编辑文件。
- 练习 `Vim` 三大模式的切换：常规模式（`normal mode`）、插入模式（`insert mode`）、命令行模式（`commandline / cmdline / line mode`）

练习过程中，您将使用 `Vim` 创建一个新文件，并输入一些内容，最后保存。[^1]



## 2 操作指令

### 1 创建文件

先在本地打开一个命令行会话，再用 `Vim` 编辑一个名为 `myday.txt` 的新文件。在命令行输入 `vim myday.txt`，按回车键 <kbd>Enter</kbd> 确认：

```bash
vim myday.txt
```



### 2 启用插入模式

这样就打开了一个新文件，并处在 `Vim` 的常规模式（normal mode）下。按下小写的 <kbd>I</kbd> 键进入插入模式（insert mode）



### 3 给文件添加些文字

接下来输入一些内容。比如写几句话来描述您一天的开始。输入过程中如果写错了，可以用退格键 <kbd>Backspace</kbd> 进行更正。



### 4 继续添加文字内容

继续向文件添加文本，输入三件让您心怀感激的事物。写完后，按 <kbd>Esc</kbd> 键返回常规模式。



### 5 保存文件

接着保存您的变更内容。这需要在常规模式下进行。若不确定是否在常规模式，可以再按一次 <kbd>Esc</kbd> 键进行确认。下一步，输入 `:wq` + <kbd>Enter</kbd> 保存文件并退出 `Vim`。



### 6 验证文件已保存

您可以通过查看文件内容来确认是否已经保存成功。比如使用 `Vim` 编辑器打开该文件：输入 `vim myday.txt` + <kbd>Enter</kbd> 即可：

```bash
vim myday.txt
```

这样就能看到您输入并保存到文件中的内容。由于未做任何修改，也没有什么需要保存的变更内容，直接使用 `:q!` + <kbd>Enter</kbd> 键退出即可。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-01-CreatingandEditingaNewFilewithVim.pdf`

