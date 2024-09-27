# L06 Exercise 01 Creating and Editing a New File with Vim
---

【**注：本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：vimclass/Exercise-01-CreatingandEditingaNewFilewithVim.pdf**】



## 训练目标

- 练习用 vim 创建文件、编辑文件。
- 练习 vim 三大模式的切换：常规模式（normal mode）、插入模式（insert mode）、命令行模式（commandline / cmdline / line mode）

练习过程中，您将使用 vim 创建一个新文件，并输入一些内容，最后保存。



## 操作指令

### 1 创建文件

First, start a command line session on your local machine.  Next, use vim to edit a new file named myday.txt.  To do that type, **vim myday.txt** at the command line and press `<ENTER>`.

```bash
$ vim myday.txt
```

### 2 启用插入模式

You now have a new file opened and you're placed into normal mode.  Press lowercase **i** to enter the insert mode.

### 3 给文件添加些文字

Next, start typing.  Write a few sentences about the beginning of your day.  If you make a mistake while you're typing, you can press the backspace key to correct any errors.

### 4 继续添加文字内容

Continue adding text to the file by typing three things you're grateful for.  Once you're done typing, press Escape to enter normal mode.

### 5 保存文件

Next save your changes.  You should already be in normal mode, but if you're not sure you can also press the Escape key again to be sure you are in normal mode.  Next, type **`:wq<ENTER>`** to save the file and exit vim.

### 6 验证文件已保存

You can verify that you've saved your changes by looking at the contents of the file.  One way to do that is to use the vim editor to open the file.  Type **`vim myday.txt<ENTER>`**.

```bash
$ vim myday.txt
```

You'll now see what you typed and saved into the file.  Because we aren't making any changes and don't want to save any changes, we can exit with **`:q!<ENTER>`**.
