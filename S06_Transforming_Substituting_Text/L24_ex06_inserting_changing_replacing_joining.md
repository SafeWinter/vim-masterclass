# L24 Exercise 06 - Inserting, Changing, Replacing, and Joining
---



## 1 训练目标

练习 `Vim` 中的文本插入、变更、替换与连接。[^1]



## 2 操作指令

### 2.1. 打开 insert-practice.txt 文件

用 `Vim` 打开源码包内的练习文件 `insert-practice.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim insert-practice.txt
```



### 2.2. 练习 `i` 命令

切记，`i` 命令会在当前光标位置进入 `Vim` 插入模式。利用 `i` 命令在文件第一行开头插入一些文字。例如 `"vim"`，然后按 <kbd>Escape</kbd> 键返回常规模式。



### 2.3. 练习 `I` 命令

按 <kbd>2</kbd><kbd>J</kbd> 将光标下移至这一行文本：

```markdown
<= What is your favorite color?
```

利用 `I` 命令在行首插入文字来回答上面的提问。例如，答案为 `blue`（蓝色），然后按 <kbd>Escape</kbd> 键回到常规模式。



### 2.4. 练习 `a` 命令

按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，并练习在 `><` 符号之间输入您的姓名。

```markdown
Enter your name here =><=
```

为此，需要用 <kbd>F</kbd><kbd>></kbd> 定位到 `>` 字符下（注意：`f` 命令将在第 L23 课 Vim 文本检索中详细介绍，这里用于让光标快速定位到同一行的指定字符位置）。然后利用 `a` 命令从光标的后面进入插入模式。输入任意姓名，并按 <kbd>Escape</kbd> 键回到常规模式。



### 2.5. 练习 `A` 命令

按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，然后通过 `A` 命令在该行末尾进入插入模式，接着输入姓名。输入完毕，按 <kbd>Escape</kbd> 键回到常规模式。

```markdown
Enter your name here:
```



### 2.6. 练习 `o` 命令

按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，键入 <kbd>O</kbd> 在当前行的下一行进入插入模式，然后输入您最喜爱的一部电影名。输入完毕，按 <kbd>Escape</kbd> 键回到常规模式。

```markdown
One the line below, type the name of your favorite movie.
```



### 2.7. 练习 `O` 命令

按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，键入 <kbd>Shift</kbd><kbd>O</kbd> 在当前行的上一行进入插入模式，然后输入 `vim`。按 <kbd>Escape</kbd> 键回到常规模式。

```markdown
^^^ One the line above, type the name of the editor you are using.
```



### 2.8. 练习 `j` 命令

按 <kbd>3</kbd><kbd>J</kbd> 定位到下面这行文本，尝试连接下列两行文本：

```markdown
This line belongs
with the one below it.
```

完成相关操作后，文字将显示在同一行上：

```markdown
This line belongs with the one below it.
```

为此，需要键入 <kbd>Shift</kbd><kbd>J</kbd>。



### 2.9. 练习 `R` 命令

按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，试将单词 `her` 替换为 `our`。

替换前：

```markdown
Vim is her favorite editor.
```

替换后：

```markdown
Vim is our favorite editor.
```

先按 <kbd>Shift</kbd><kbd>F</kbd><kbd>H</kbd> 进行反向查，找将光标移至单词 `her` 中的 `h` 下方，然后通过 `R` 命令进入替换模式，并输入 `our`。最后按 <kbd>Escape</kbd> 键回到常规模式。



### 2.10. 练习 `r` 命令

拟对如下文本行进行更改：

```markdown
I have a white car.
```

更改后变为：

```markdown
I have a white cat.
```

先按 <kbd>2</kbd><kbd>J</kbd> 定位到下面这行文本，再用 <kbd>F</kbd><kbd>R</kbd> 将光标定位到单词 `car` 的 `r` 字符下（注意：`f` 命令将在第 L23 课 Vim 文本检索中详细介绍，这里用于让光标快速定位到同一行的指定字符位置）。接着按 <kbd>R</kbd> 键启用替换命令，然后输入字符 `t` 完成替换。 



### 2.11. 练习 `c` 命令

试将下列句子中的 `great` 变更为 `brilliant`：

```markdown
I am having a great time in this vim class!
```

最终变为：

```markdown
I am having a brilliant time in this vim class!
```

先用 <kbd>/</kbd><kbd>G</kbd><kbd>R</kbd> + <kbd>Enter</kbd> 将光标定位到单词 `great` 的 `g` 字符下（注意：`/` 命令将在第 23 课 Vim 文本检索中详细介绍，这里仅用于将光标快速定位到 `great` 的 `g` 位置，支持跨行检索）。接着按 <kbd>C</kbd><kbd>W</kbd>（即 **c**hange **w**ord，更改单词），再输入单词 `brilliant` 完成变更。最后，按 <kbd>Escape</kbd> 键回到常规模式。

接着，将下列句子中的 `myself.` 改为 `everyone!`：

```markdown
I love myself.
```

这是编辑后的效果：

```markdown
I love everyone!
```

先将光标定位到 `myself` 的 `m` 字符上，可通过 `/my` + <kbd>Enter</kbd> 实现（注意：`/` 命令将在第 23 课 Vim 文本检索中详述，这里仅用于快速定位光标到指定位置，且支持跨行检索）。然后输入 `cW`，实现带标点更改单词；接着再输入 `everyone!` 即可。最后，按 <kbd>Escape</kbd> 键回到常规模式（注意：本例也可以通过 `c$` 或 `C` 命令实现与 `cW` 命令相同的效果）。

最后，试将下列一整行文字改为任意内容：

```markdown
Type something wonderful here.
```

先按 <kbd>2</kbd><kbd>J</kbd> 定位到这行文本，然后键入 `cc` 命令，以实现整行更改。然后输入任意内容，例如 `The sky is beautiful!`，并按 <kbd>Escape</kbd> 键返回常规模式。



### 2.12. 用 `~` 命令变更大小写

将下列文字中单词 `monday` 的首字母改为大写：

```markdown
monday <= The "m" is supposed to be in uppercase.
```

为此，需按 `/m` + <kbd>Enter</kbd> 进行正向检索，将光标定位到 `m` 处；然后键入 <kbd>~</kbd> 完成大小写转换。

将下列文字中的单词 `shout` 全部改为大写形式：

```markdown
Don't shout.  It's not nice.
```

为此，需按 `/sh` + <kbd>Enter</kbd> 进行正向检索，将光标定位到 `s` 下方；然后键入 <kbd>G</kbd><kbd>~</kbd><kbd>W</kbd> 实现大写转换操作。

再对下面一整行内容切换大小写：

```markdown
mONDAY'S START BETTER WITH coffee.
```

最终效果如下：

```markdown
Monday's start better with COFFEE.
```

为此，先按 <kbd>2</kbd><kbd>J</kbd> 定位到这行文本的任意位置，然后键入 <kbd>G</kbd><kbd>~</kbd><kbd>~</kbd> 完成整行字符的大小写切换。



### 2.13. 练习 `U` 命令

试将下列文字中的单词 `Shout` 改为 `SHOUT`：

```markdown
Don't Shout.  It's just too loud.
```

为此，先用 `/S` + <kbd>Enter</kbd> 正向检索，将光标定位到 `S` 下方；然后输入命令 `gUw`，完成单词的大写转换操作。

接着，在下一行再尝试一次，不过这次要改用 `gUW` 命令。



### 2.14. 练习 `u` 命令

将下列文字中的单词 `Whisper` 改为小写的 `whisper`：

```markdown
Please Whisper.
```

为此，先用 `/W` + <kbd>Enter</kbd> 正向检索，将光标放在 `W` 下方；然后输入 `guw` 完成小写转换（注意：本例中也可以直接使用 `~` 命令）。



### 2.15. 重复命令练习

在下列文字的下面一行输入 80 个星号（\*）：

```markdown
Create a line of asterisks below:
```

为此，先用 <kbd>3</kbd><kbd>J</kbd> 将光标定位到该行文本的下一行；然后输入 <kbd>8</kbd><kbd>0</kbd><kbd>I</kbd> 进入插入模式，拟重复执行 80 次；再键入 <kbd>\*</kbd> 插入星号。最后按 <kbd>Escape</kbd> 键切回常规模式，并查看 Vim 自动插入的 80 个星号效果。

接着，再在下列文本行的下方三行，每行各插入一个连字符 `-`：

```markdown
Create 3 lines that begin with "-" below:
```

为此，先用 <kbd>2</kbd><kbd>J</kbd> 定位到该行文本；然后使用 `o` 命令，键入 <kbd>3</kbd><kbd>O</kbd>，并在新行中输入一个连字符 <kbd>-</kbd>；最后按 <kbd>Escape</kbd> 键切回常规模式，并查看 Vim 自动生成的另两行效果。



## 3 自由练习

鼓励自行尝试一些组合练习。最好是有个现成的文件需要修改，然后用 `Vim` 打开，用学到的文本插入、更改、替换与连接的知识来操作文件内容。



## 4 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。





---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-06-InsertingChangingReplacingandJoining.pdf`





