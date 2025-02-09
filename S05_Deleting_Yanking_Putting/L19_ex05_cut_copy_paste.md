# L19 Exercise 05 - Cut, Copy and Paste
---



## 1 训练目标

练习 `Vim` 中的剪切、复制、粘贴；熟悉 `register` 寄存器。[^1]



## 2 操作指令

### 2.1 打开 dyp.txt 文件

用 `Vim` 打开源码包内的练习文件 `dyp.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim dyp.txt
```



### 2.2 交换文件的头两行

首先，用 <kbd>D</kbd><kbd>D</kbd> 删除文件首行。该行会进入默认寄存器。然后使用 `p` 命令将该行粘贴到新的这行下面。

操作前，这两行应该像这样：

```markdown
This was originally the first line in the file.
This was originally the second line in the file.
```

操作后应该变为这样：

```markdown
This was originally the second line in the file.
This was originally the first line in the file.
```



### 2.3 将文件首行 put 到文件其他为止

切记：默认寄存器的内容可以多次使用。将文件最初的首行放到这一行下面：

```markdown
What was the first line in the file originally?  Place it below:
```

方法：先定位到这一行，然后按 <kbd>P</kbd> 执行 `put` 命令。



### 2.4 练习在光标位置的上方粘贴文本行

将最初的首行内容粘贴到这一行的上方：

```markdown
What was the first line in the file originally?  Place it above:
```

方法：先定位到这一行，然后按下 <kbd>Shift</kbd> + <kbd>P</kbd>。



### 2.5 通过交换字符顺序更正存在的笔误

光标定位到这一行的字母 `e` 上：

```markdown
teh
```

交换 `e` 和 `h` 的位置，让其变为 `the`。方法：输入 <kbd>X</kbd> 删除 `e`，然后输入 <kbd>P</kbd> 将其粘贴到紧挨当前光标后面的位置。

重复上述流程更正下面四行拼错或输错的内容：

```markdown
psell = spell
vmi = vim
wrod = word
taht = that
```



### 2.6 交换单词

将如下这行由：

```markdown
second, First, third.
```

变为：

```markdown
First, second, third.
```

方法：光标移至行首位置、即单词 `second` 的 `s` 上；然后使用 `dW` 命令（注意 `W` 是大写形式）将该单词连同后面的逗号一并删除；再用 <kbd>W</kbd> 令光标移至单词 `third` 的开头位置；最后使用 <kbd>Shift</kbd> + <kbd>P</kbd> 在当前光标位置的前方粘贴默认寄存器内的文本内容。



### 2.7 重复某一行

重复下面这一行，并将其复制到它的下方：

```markdown
Duplicate this line.
```

方法：光标定位到该行，使用 `yy` 将其 yank 到默认寄存器。接着使用 `p` 命令粘贴到该行的下方。



### 2.8 重复某个单词

重复下面这一行的单词 `really, really,`：

```markdown
I really, really, love vim!
```

方法：光标定位到第一个单词 `really` 的字母 `r` 上；再用 `y2W` 命令将这两个单词（包括标点）复制到默认寄存器；然后用 <kbd>Shift</kbd> + <kbd>P</kbd> 粘贴到当前光标的前方。此时这行文本应该变成这样：

```markdown
I really, really, really, really, love vim!
```



### 2.9 使用数字寄存器（register）

将文本 `TODO` 粘贴到文件中所有以 `Fix this` 开头的文本行上方；同时，删除所有标注了 `Delete this` 的行；从光标当前位置开始，向下浏览文件，交替执行删除与粘贴操作。

方法：先用 `yy` 复制 `TODO` 那行文本；再用 `2dd` 删除两行标有 `Delete this` 的文本行；光标定位到含有 `Fix this` 的行，然后将 `TODO` 粘贴到它的上方。这一步需要用到 `0` 号寄存器中保存的上一次复制的文本，输入 `"0P` 即可。重复上述操作，直到所有以 `Fix` 开头的行上方都有一个 `TODO`、同时所有包含 `Delete` 的行都被删除。



### 2.10 使用命名寄存器

先将以下这行文本存到 `"j` 寄存器中：

```markdown
Yank this line into the "j register.
```

方法：光标定位到该行任意位置，输入 `"jyy`。



然后再将下面这行内容放入 `"f` 寄存器。

```markdown
Yank this line into the "f register.
```

方法：光标定位到该行任意位置，输入 `"fyy`。



然后使用命令 `"jp`，将 `"j` 寄存器中的内容粘贴到下面这行的下方：

```markdown
Put the contents of the "j register below:
```



再用 `"fp` 将 `"f` 寄存器中的文本内容粘贴到下面这一行的下方：

```markdown
Put the contents of the "f register below:
```



将下面这行内容追加到 `"j` 寄存器内：

```markdown
Append this line to the "j register.
```

方法：光标定位到该行任意位置，并输入命令 `"Jyy`（注意 `J` 为大写字母）。



再将下列一行文本追加到 `"f` 寄存器内：

```markdown
Append this line to the "f register.
```

方法：光标定位到该行任意为止，输入命令 `"Fyy`（注意 `F` 为大写字母）。



使用 `:reg` + <kbd>Enter</kbd> 查看所有寄存器中的内容。例如查看 `"j` 和 `"f` 寄存器，使用命令 `:reg jf` + <kbd>Enter</kbd>。

然后使用 `"jp` 命令，将 `"j` 寄存器中的内容粘贴到下面这行文字的下方：

```markdown
Put the contents of the "j register below:
```



接着，使用 `"fp` 命令，将 `"f` 寄存器中的内容粘贴到下面这行文字的下方：

```markdown
Put the contents of the "f register below:
```



### 2.11 撤销与重做练习

删除以下三行内容：

```markdown
ONE)
TWO)
THREE)
```

方法：光标定位到第一行，输入 `3dd`；使用 `u` 命令撤销删除；注意看三行内容是怎么还原的。

通过 <kbd>Ctrl</kbd> + <kbd>R</kbd> 重复执行刚才的删除命令，此时这三行又被重新删除。

向文件插入一个新行：先使用 `i` 命令进入插入模式；然后在 Vim 中输入一些句子，例如下面这句话：

```markdown
Vim is fun!
```

按下 <kbd>Escape</kbd> 键返回正常模式。使用 `u` 命令撤销刚才输入的文本。然后使用 <kbd>Ctrl</kbd> + <kbd>R</kbd> 重新插入刚才的文本内容。



## 3 自由练习

鼓励自行尝试一些组合练习。最好是有个现成的文件需要修改，然后用 Vim 打开，用学到的删除、复制、粘贴去操作文件内容。



## 4 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-05-CutCopyPaste.pdf`
