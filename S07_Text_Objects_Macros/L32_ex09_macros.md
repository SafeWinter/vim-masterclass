# L32 Exercise 09 - Macros
---

## 1 训练目标

练习 `Vim` 中的宏（`macro`）的创建与使用。[^1]



## 2 操作指令

### 2.1. 打开 macros-practice.txt 文件

用 `Vim` 打开源码包内的练习文件 `macros-practice.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim macros-practice.txt
```



### 2.2. 将旧版 Python 代码转换为新版写法

给定一组旧版 Python 代码（`v2.6` 及以前版本），试将其改为新版写法（`v3.0` 即以上版本）：将 `print` 语句改为 `print()` 函数。也就是说，需要对以下各行作如下处理：

由修改前的：

```python
print "Macros are very fun!"
```

统一改为：

```python
print("Macros are very fun!")
```

Let's do this with a macro.  By the way, it's not important to know anything about Python.  The goal here is to give you a practical example for you to practice your Vim macros skills with.
让我们用宏来做这个。顺便说一下，了解 Python 并不重要。这里的目标是给你一个实际的例子，让你练习你的 Vim 宏技能。

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor on the line that reads:  print "Macros are very fun!"
  将光标放在以下行上： print "Macros are very fun!"
- Start recording into the **"a** register with **qa**.
  开始录制到“a register with qa”。
- Normalize your cursor position to the beginning of the line by typing **0**.
  通过输入 0 将光标位置归一化到行首。
- Position the cursor at the next space with **f<SPACE>**.
  将光标定位到下一个空格，使用 f。
- Replace the space with an opening parenthesis with **r(**.
  将空格替换为左括号 r(。
- Append a closing parenthesis to the line with **A)** and press **<ESCAPE>** to return to normal mode.
  在带有 A) 的行末添加一个右括号，然后按 返回正常模式。
- Now position the cursor on the next line with **j** so the macro can be easily repeated.
  现在将光标移动到下一行，使用 j 以便宏可以轻松重复。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"a** register with **:reg a<ENTER>**.  Here is what it should look like:
您可以通过查看“a 寄存器，使用 :reg a 来检查宏的内容。它应该是这样的：

`"a  0f r(A)^[j`

Play your macro on the next line by typing **@a**.  Use **@@** to repeat the macro on.  Continue repeating the macro with **@@** on the remaining print statements.
在下一行通过输入 @a 播放你的宏。使用 @@ 重复宏。继续在剩余的打印语句中使用 @@ 重复宏。

NOTE: The solution provided above is not the only way to accomplish this task!  One simple example is replacing **f<SPACE>** with **t"** in the macro.  Both perform the same act of positioning the cursor under the space.  As long as you get the desired results you're after, that's all that matters.
注意：上述提供的解决方案并不是完成此任务的唯一方法！一个简单的例子是在宏中将 f 替换为 t"。两者都执行将光标定位在空格下的相同操作。只要你得到你想要的结果，这就是最重要的。

### 2.3. 从列表中批量创建 Shell 脚本

Let's say you have a list of users and you want to perform the same set of actions on each of those users.  One way to accomplish this is to record a macro that performs the required command for one user and apply that macro to the rest of the list.
假设你有一个用户列表，并且你想对每个用户执行相同的一组操作。实现这一点的一种方法是录制一个宏，该宏为一个用户执行所需的命令，然后将该宏应用于列表中的其余用户。

The goal is to turn this text:
目标是将这段文本转换为：

```markdown
jason
sophia
jack
emma
ava
```

改为：

```bash
passwd -l jason && echo jason >> locked_users.txt
passwd -l sophia && echo sophia >> locked_users.txt
passwd -l jack && echo jack >> locked_users.txt
passwd -l emma && echo emma >> locked_users.txt
passwd -l ava && echo ava >> locked_users.txt
```

You could use those commands on a Linux system to lock each of the user accounts and add the account names to the locked_users.txt file.  Of course, it's not important what these commands do as we're interested in Vim, but I wanted to provide you with a practical example.
您可以在 Linux 系统上使用这些命令来锁定每个用户帐户，并将帐户名称添加到 locked_users.txt 文件中。 当然，这些命令的作用并不重要，因为我们对 Vim 感兴趣，但我想给您提供一个实际的例子。

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor on the line that contains "jason".
  将光标放在包含“jason”的行上。
- Start recording into the **"b** register with **qb**.
  开始录制到 "b register with qb。
- Yank the user name into the default register with **yaw**.
  将用户名用 yaw 拉入默认寄存器。
- Start insert mode at the beginning of the line with **I**. Now type the text "passwd -l " and press **<ESCAPE>**.
  在行首以 I 开始插入模式。现在输入文本 "passwd -l " 并按 。
- Next, start insert mode at the end of the line with **A** and type " && echo ".  Press **<ESCAPE>** to return to normal mode.
  接下来，在行末按 A 进入插入模式，并输入 " && echo "。按 返回到正常模式。
- Next, paste the contents of the unnamed register after the cursor position with **p**.
  接下来，在光标位置后使用 p 粘贴未命名寄存器的内容。
- Continue appending by typing **a**, and then typing " >> locked_users.txt" followed by **<ESCAPE>**.
  继续通过输入 a，然后输入 " >> locked_users.txt" 并按 继续追加。
- Now position the cursor on the next line with **j** so the macro can be easily repeated.
  现在将光标移动到下一行，使用 j 以便宏可以轻松重复。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"b** register with **:reg b<ENTER>**.  Here is what it should look like:
您可以通过查看“b 寄存器”来检查宏的内容，方法是输入 :reg b。它应该是这样的：

`"b  yawIpasswd -l ^[A && echo ^[pa >> locked_users.txt^[j`

Play your macro on the next line by typing **@b**.  You can probably see that there are three more items in this list, so use **3@b** to repeat the macro four times.
在下一行通过输入 @b 来播放你的宏。你可能会看到这个列表中还有三个项目，所以使用 3@b 来重复宏四次。



### 2.4. 对电话号码作格式化处理

接下来，创建一个宏，将如下所示的电话号码：

`2798265253`

转换为以下符合美国人书写惯例的统一格式：

`(279) 826-5253`

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor on the line that contains "2798265253".
  将光标放在包含“2798265253”的行上。
- Start recording into the **"p** register with **qp**.
  开始录制到“p 寄存器”中，使用 qp。
- Start insert mode at the beginning of the line with **I**.
  在行首按 I 进入插入模式。
- Type an opening parenthesis **(** and press **<ESCAPE>** to return to normal mode.
  输入一个左括号 ( 并按 返回正常模式。
- Position the cursor under the 9 by typing **l** 3 times.
  将光标放在 9 下方，输入 l 三次。
- Type **a** to append text after the cursor and type **)<SPACE>**.  Press **<ESCAPE>** to return to normal mode.
  输入 a 以在光标后追加文本，然后输入 )。按 返回正常模式。
- Position the cursor under the 6 by typing **l** 3 times.
  将光标放在 6 下方，输入 l 三次。
- Type **a-** to append a hyphen and press **<ESCAPE>** to return to normal mode.
  输入 a- 以添加一个连字符，然后按 返回正常模式。
- Now position the cursor on the next line with **j** so the macro can be easily repeated.
  现在将光标移动到下一行，使用 j 以便宏可以轻松重复。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"p** register with **:reg p<ENTER>**.  Here is what it should look like:
您可以通过输入 :reg p 来查看宏的内容。它应该是这样的：

`"p  I(^[llla) ^[llla-^[j`

Because there is a long list of phone numbers that scroll off the bottom of your screen you can't easily know how many times you need to apply the macro.  Also, repeating @@ could take quite awhile.  So, get the range you need to apply the macro to.  Turn on line numbering with **:set nu<ENTER>**.  Note that your cursor is currently on line 25.  Now page down to the end of the list of phone numbers with **Ctrl-f**.  You'll find the last phone number is on line 73.
因为有一长串电话号码滚动出屏幕底部，所以你无法轻易知道需要应用宏多少次。此外，重复@@可能会花费相当长的时间。因此，获取你需要应用宏的范围。通过:set nu开启行号。请注意，你的光标当前在第 25 行。现在按 Ctrl-f 向下翻页到电话号码列表的末尾。你会发现最后一个电话号码在第 73 行。

Execute the macro over this range using the **normal** command.  Type **:25,73 normal @p<ENTER>**. Now check that the macro was executed over that entire range by paging up with **Ctrl-b**.
使用正常命令在此范围内执行宏。输入 :25,73 normal @p。现在通过按 Ctrl-b 向上翻页检查宏是否在整个范围内执行。

### 2.5. 从日志文件中提取重要数据

The next set of lines in the file contain system logs from a Linux server.  Specifically these lines are logs of blocked connection attempts by the local Linux firewall.  Your goal is to extract the timestamp, the source IP address of the connection attempt, and the destination port.
文件中的下一组行包含来自 Linux 服务器的系统日志。具体来说，这些行是本地 Linux 防火墙阻止的连接尝试的日志。您的目标是提取时间戳、连接尝试的源 IP 地址和目标端口。

The source IP address follows "SRC=".  Example: SRC=190.18.193.152
源 IP 地址在“SRC=”后面。 示例：SRC=190.18.193.152

The destination port follows "DPT=".  Example: DPT=23
目标端口跟随 "DPT="。 示例：DPT=23

This line: 这一行：

```markdown
Jan 13 09:57:01 www1 kernel: [3947771.808744] [BLOCK] IN=eth0 OUT= MAC=e6:e9:2d:04:b6:95:3c:8a:b0:0d:6f:f0:08:00 SRC=190.18.193.152 DST=2.5.9.1 LEN=40 TOS=0x02 PREC=0x00 TTL=51 ID=25120 PROTO=TCP SPT=12502 DPT=23 WINDOW=4078 RES=0x00 SYN URGP=0
```

Will be narrowed down to just this comma separated value line:
将仅缩小到这一逗号分隔值行：

```markdown
Jan 13 09:57:01,190.188.193.152,23
```

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor on the line that starts with "Jan 13 09:57:01".
  将光标放在以“Jan 13 09:57:01”开头的行上。
- Start recording into the **"l** register with **ql**.
  开始录制到 "l register with ql。
- Normalize your cursor position to the beginning of the line by typing **0**.
  通过输入 0 将光标位置归一化到行首。
- Position your cursor on the space just after the time stamp by typing **tw**.
  将光标放在时间戳后面的空格上，输入 tw。
- Now delete all the text up to "SRC=".  You can do this with **dtS**.
  现在删除所有文本直到 "SRC="。你可以用 dtS 来做到这一点。
- Now delete SRC with **dw**.
  现在用 dw 删除 SRC。
- Next, replace "=" with a comma: **r,**.
  接下来，将 "=" 替换为逗号：r,。
- Position the cursor after the IP address with **f<SPACE>**.
  将光标放在 IP 地址后面，使用 f。
- Delete the text up to "DPT=" with **d/DPT<ENTER>**.
  使用 d/DPT 删除 "DPT=" 之前的文本。
- Now delete DPT with **dw**.
  现在删除 DPT 和 dw。
- Next, replace "=" with a comma: **r,**.
  接下来，将 "=" 替换为逗号：r,。
- Position the cursor after the port number with **f<SPACE>**.
  将光标放在端口号后面，按 f。
- Delete the remaining text on the line with **D**.
  删除 D 所在行的其余文本。
- Now position the cursor on the next line with **j** so the macro can be easily repeated.
  现在将光标移动到下一行，使用 j 以便宏可以轻松重复。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"l** register with **:reg l<ENTER>**.  Here is what it should look like:
您可以通过输入 :reg l 来查看宏的内容。它应该是这样的：

`"l   0twdtSdwr,f d/DPT^Mdwr,f Dj`

As always, there are other ways to accomplish the same task.  Just one simple example is using **2cw,<ESCAPE>** to change "SRC=" to "," instead of using **dwr,**.  Take a moment and think of other ways to alter this macro and get the same result.
和往常一样，还有其他方法可以完成相同的任务。一个简单的例子是使用 2cw, 将 "SRC=" 改为 ","，而不是使用 dwr,。花点时间想想其他方法来修改这个宏并获得相同的结果。

Test your macro on the next line by typing **@l**.  If it looks correct, continue with **@@** until all the lines are in the desired format.
在下一行测试你的宏，输入 @l。如果看起来正确，请继续输入 @@，直到所有行都达到所需格式。

### 2.6. 将多行数据压缩为一行

Remember that macros are just a series of recorded keystrokes.  Even though you've been working on macros that manipulate single lines, you can as easily manipulate multiple lines.  Let's say you want to turn these three lines into one line.
请记住，宏只是一系列录制的按键。尽管您一直在处理操作单行的宏，但您同样可以操作多行。假设您想将这三行变成一行。

Before: 之前：

```markdown
Country China
1,380,950,000 people
```

After: 之后：

```markdown
1,380,950,000;China
```

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor on the line that reads "Country China".
  将光标放在写有“Country China”的行上。
- Start recording into the **"c** register with **qc**.
  开始录制到“c 寄存器”中，使用 qc。
- Normalize your cursor position to the beginning of the line by typing **0**.
  通过输入 0 将光标位置归一化到行首。
- Delete the word "Country" with **dw**.
  用 dw 删除“Country”这个词。
- Move to the line below with **j**.
  用 j 移动到下一行。
- Cut the number into the unnamed register with **dW**.
  将数字放入未命名的寄存器中，使用 dW。
- Move up to the original line with **k**.
  使用 k 移动到原始行。
- Paste the number before your cursor position with **P**.
  在光标位置之前粘贴数字，使用 P。
- Replace the space with a semicolon by typing **r;**.
  将空格替换为分号，输入 r;。
- Move to the line below with **j**.
  用 j 移动到下一行。
- Delete the current line and the next line with **2dd**.
  使用 2dd 删除当前行和下一行。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"c** register with **:reg c<ENTER>**.  Here is what it should look like:
您可以通过输入 :reg c 来查看宏的内容。它应该是这样的：

`"c  0dwjdWkPr;j2dd`

Now use a count to repeat the macro 4 more times to format the rest of the data in this set.  Type **4@c**.
现在使用计数将宏重复 4 次，以格式化此数据集中的其余数据。输入 4@c。

As always, there are multiple ways to achieve the same result in Vim.
和往常一样，在 Vim 中有多种方法可以实现相同的结果。

### 2.7. 从 HTML 中提取数据

Here are a list of links (\<a> tags) on a single line of HTML.
这里是一行 HTML 中的链接列表（\<a>标签）。

```html
<a href="#">@armyspy.com</a><a href="#">@cuvox.de</a><a href="#">@dayrep.com</a><a href="#">@einrot.com</a><a href="#">@fleckens.hu</a><a href="#">@gustr.com</a><a href="#">@jourrapide.com</a><a href="#">@rhyta.com</a><a href="#">@superrito.com</a><a href="#">@teleworm.us</a>
```

The goal is convert those links to the following:
目标是将这些链接转换为以下内容：

```markdown
armyspy.com
cuvox.de
dayrep.com
einrot.com
fleckens.hu
gustr.com
jourrapide.com
rhyta.com
superrito.com
teleworm.us
```

Here is one way to accomplish this task:
这里有一种方法可以完成这个任务：

- Place your cursor at the beginning of the line that starts with "<a".
  将光标放在以"
- Start recording into the **"q** register with **qq**.
  开始录制到“q”寄存器，使用 qq。
- Delete the text up to and including "@" with **df@**.
  删除文本直到并包括"@"，使用 df@。
- Position the cursor under the "<" with **f<**.
  将光标放在"<"下方，使用 f<。
- Replace "</a>" with **<ENTER>** by typing **cf><ENTER><ESCAPE>**.
  将 "" 替换为 ，方法是输入 cf>。
- Finally type **q** to stop recording the macro.
  最后输入 q 以停止录制宏。

You can examine the contents of your macro by looking at the **"q** register with **:reg q<ENTER>**.  Here is what it should look like:
您可以通过输入 :reg q 来查看宏的内容。它应该是这样的：

`"q  df@f<cf>^M^[`

Execute the macro with **@q**.  Keep repeating the macro with **@@** until you are left with the desired text.
使用 @q 执行宏。继续使用 @@ 重复宏，直到得到所需的文本。



## 3 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-09-Macros.pdf`



