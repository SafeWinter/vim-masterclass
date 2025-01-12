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

为此，需要按 <kbd>J</kbd> 键。



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

先按 <kbd>F</kbd><kbd>H</kbd> 将光标移至单词 `her` 中的 `h` 下方，然后通过 `R` 命令进入替换模式，并输入 `our`。最后按 <kbd>Escape</kbd> 键回到常规模式。



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

In the following sentence, change "myself." to "everyone!":
在下面的句子中，将 "我自己 "改为 "每个人！"：

```markdown
I love myself.
```

After your edit, the line should look like this:
编辑后，该行应如下所示：

```markdown
I love everyone!
```

First, position your cursor under "m" in the word "myself".  You can do that by performing a forward search with **/my<ENTER>**.  (NOTE: The **/** command is covered in the searching lesson.  For now, know that it moves your cursor to the next matching string you specify, even if it is on a different line in the file.)  Now type **cW**, which allows you to change a word including the punctuation that follows.  Next type "everyone!".  Finally press **<Escape>** to return to normal mode.  (NOTE: You could have also used the **c$** or **C** command in this example to achieve the same result as the **cW** command.
首先，将光标放在 "我自己 "中的 "m "下面。您可以使用 /my进行前向搜索。(注意："/"命令将在 "搜索 "一课中介绍。现在只需知道它能将光标移动到你指定的下一个匹配字符串，即使该字符串在文件的不同行上）。现在输入 cW，它允许你更改一个单词，包括后面的标点符号。接着输入 "everyone!"。最后按 键返回正常模式。(注意：在本例中也可以使用 c$ 或 C 命令来达到与 cW 命令相同的效果。

Change this entire line of text to anything you want to type:
将整行文字改成你想输入的任何内容：

```markdown
Type something wonderful here.
```

First, place your cursor anywhere on the line with **2j**.  Next, use the command **cc** which allows you to change the entire line.  Type anything you want.  For example, "The sky is beautiful!".  Finally press **<Escape>** to return to normal mode.
首先，将光标放在 2j 行的任意位置。然后，使用 cc 命令，该命令允许您更改整行。输入任何你想要的内容。例如，"天空真美！"。最后按 键返回正常模式。

### 2.12. 用 `~` 命令变更大小写

Capitalize the first letter of the word "monday" on this line:
请将这一行中 "monday "一词的第一个字母大写：

```markdown
monday <= The "m" is supposed to be in uppercase.
```

To do that place your cursor under the "m" by performing a forward search with **/m<ENTER>**.  Next type **~** to perform the case switch case operation.
为此，使用 /m执行前向搜索，将光标放在 "m "下。然后键入 ~ 执行大小写转换操作。

Capitalize the entire word "shout" on this line:
将这一行中的 "呐喊 "一词全部大写：

```markdown
Don't shout.  It's not nice.
```

To do that place your cursor under the "s" by performing a forward search with **/sh<ENTER>**.  Next type **g~w** to perform the case switch case operation on the word motion.
为此，用 /sh 执行前向搜索，将光标放在 "s "下面。然后键入 g~w 对单词 "motion "执行大小写转换操作。

Switch the case of the entire following line:
切换下面整行的大小写：

```markdown
mONDAY'S START BETTER WITH coffee.
```

After your edit it will look like this:
编辑后，它将看起来像这样：

```markdown
Monday's start better with COFFEE.
```

To make that change, place your cursor anywhere on the line with **2j**.  Next type **g~~** to switch the case of the entire line.
要进行更改，请将光标放在 2j 行的任意位置。然后输入 g~~ 以切换整行的大小写。

### 2.13. Using the U command 使用 U 命令

On the following line, change the word "Shout" to "SHOUT":
在下一行，将 "Shout "改为 "SHOUT"：

```markdown
Don't Shout.  It's just too loud.
```

To do that place your cursor under the "S" by performing a forward search with **/S<ENTER>**.  Next type **gUw** to perform the uppercase operation on the word motion.
为此，请使用 /S向前搜索，将光标放在 "S "下面。然后输入 gUw，对单词 motion 执行大写操作。

Try it again on the next line, but this time use **gUW**.
在下一行再试一次，但这次使用 gUW。

### 2.14. 练习 `u` 命令

On the following line, change the word "Whisper" to "whisper":
在下一行中，将 "Whisper "改为 "whisper"：

```markdown
Please Whisper.
```

To do that place your cursor under the "W" by performing a forward search with **/W<ENTER>**.  Next type **guw** to perform the lowercase operation on the word motion.  (NOTE you could have also just used the **~** in this case.)
为此，用 /W 执行前向搜索，将光标放在 "W "下面。然后输入 guw，对单词 motion 执行小写操作。(注意，在这种情况下也可以直接使用 ~）。

### 2.15. 重复命令练习

One line below the following line, create a new line that contains 80 asterisks (\*).
在下面一行的下面，新建一行，包含 80 个星号 (\*)。

```markdown
Create a line of asterisks below:
```

To do that place your cursor one line below it.  You can use **3j**, for example.  Now enter insert mode with a count of 80 by typing **80i**.  Next type ***** to insert an asterisk.  Finally press **<Escape>** to return to normal mode and watch vim insert that asterisk 80 times for you.
为此，请将光标置于其下一行。例如，可以使用 3j。现在输入 80i，进入插入模式，计数为 80。然后输入 * 插入星号。最后按下 返回正常模式，并观看 vim 为你插入星号 80 次。

One line below the following line, create 3 new lines that contain a hyphen (-).
在下面一行的下面，新建 3 行，行中包含一个连字符 (-)。

```markdown
Create 3 lines that begin with "-" below:
```

To do that place your cursor on the line by typing **2j**.  Now use the o command with a count of 3  typing **3o**.  Next type **-** to insert a hyphen on the new line.  Finally press **<Escape>** to return to normal mode and watch vim insert that line 2 more times for you.
为此，请将光标放在该行上，键入 2j。现在使用 o 命令，输入 3o。接着输入 - 在新行插入一个连字符。最后按下 返回正常模式，并观看 vim 为你插入该行 2 次。



## 3 自由练习

鼓励自行尝试一些组合练习。最好是有个现成的文件需要修改，然后用 `Vim` 打开，用学到的文本插入、更改、替换与连接的知识来操作文件内容。



## 4 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。





---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-06-InsertingChangingReplacingandJoining.pdf`





