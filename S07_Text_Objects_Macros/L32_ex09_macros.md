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

给定一组旧版 Python 代码（`v2.6` 及以前版本），试将其改为新版写法（`v3.0` 即以上版本）：将 `print` 语句改为 `print()` 函数。也就是说，需要对以下各行作如下处理——

由修改前的：

```python
print "Macros are very fun!"
```

统一改为：

```python
print("Macros are very fun!")
```

下面用 `Vim` 宏来实现。顺便提一下，本练习无需了解 `Python` 语法，本例旨在提供一个实际案例来练习 `Vim` 宏的相关操作。

其中一种参考方案实现如下：

- 光标定位到这一行：`print "Macros are very fun!"`
- 按 <kbd>Q</kbd><kbd>A</kbd> 启动宏录制并将其存入寄存器 `"a`；
- 按 <kbd>0</kbd> 对光标作标准化处理，统一定位到行首；
- 按 <kbd>F</kbd><kbd>Space</kbd> 将光标定位到下一处空格位置；
- 按 <kbd>R</kbd><kbd>(</kbd> 将当前空格替换为左小括号；
- 按 <kbd>Shift</kbd><kbd>A</kbd><kbd>)</kbd> 在行尾添加一个右小括号，再按 <kbd>Escape</kbd> 切回正常模式；
- 按 <kbd>J</kbd> 将光标下移一行，以便 `Vim` 宏快速重复操作；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"a` 中的录制内容，可输入命令 `:reg a` + <kbd>Enter</kbd>。内容如下：

`"a  0f r(A)^[j`

键入 <kbd>@</kbd><kbd>A</kbd> 即可对下一行运行录好的宏；若要重复执行上一次宏操作，按 <kbd>@</kbd><kbd>@</kbd> 即可。余下各行均可使用 <kbd>@</kbd><kbd>@</kbd> 重复宏的运行。

> [!note]
>
> **注意**
>
> 上述实现仅供参考，并非唯一的解决方案。例如将 <kbd>F</kbd><kbd>Space</kbd> 改为 <kbd>T</kbd><kbd>"</kbd>，也能将光标定位到同一处空格。只要能实现最终的效果就行。



### 2.3. 根据列表内容批量创建 Shell 脚本

给定一个用户列表，要求对列表中的每个用户分别执行一组相同的操作。为此，可以将某个用户的一系列操作录制为一个 `Vim` 宏，然后对其余用户执行这个宏即可。最终目标是将如下这段文本：

```markdown
jason
sophia
jack
emma
ava
```

统一改为以下形式：

```bash
passwd -l jason && echo jason >> locked_users.txt
passwd -l sophia && echo sophia >> locked_users.txt
passwd -l jack && echo jack >> locked_users.txt
passwd -l emma && echo emma >> locked_users.txt
passwd -l ava && echo ava >> locked_users.txt
```

这组命令用户锁定 `Linux` 系统中的指定用户帐号，并将其帐号名追加到一个 `locked_users.txt` 文件中。命令的含义无关紧要，关键在于 `Vim` 的用法。本练习旨在提供一个实际的应用场景。

其中一种参考方案实现如下：

- 将光标定位到 `jason` 这一行；
- 按 <kbd>Q</kbd><kbd>B</kbd> 启动宏录制，并将其存入寄存器 `"b`；
- 按 <kbd>Y</kbd><kbd>A</kbd><kbd>W</kbd> 将用户名复制（yank）到默认寄存器；
- 按 <kbd>Shift</kbd><kbd>I</kbd> 从行首进入插入模式，并输入 `passwd -l` + <kbd>Escape</kbd>；
- 按 <kbd>Shift</kbd><kbd>A</kbd> 从行尾进入插入模式，并输入 <kbd>Space</kbd> + `&&` + <kbd>Space</kbd> + `echo` + <kbd>Space</kbd> + <kbd>Escape</kbd> 返回正常模式；
- 接着，按 <kbd>P</kbd> 粘贴未命名寄存器（unnamed register）中的内容；
- 按 <kbd>A</kbd>，并输入 <kbd>Space</kbd> + `>>` + <kbd>Space</kbd> + `locked_users.txt`，再按 <kbd>Escape</kbd> 切回正常模式；
- 按 <kbd>J</kbd> 将光标下移一行，以便快速重复宏操作；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"b` 中的录制内容，可输入命令 `:reg b` + <kbd>Enter</kbd>。内容如下：

`"b  yawIpasswd -l ^[A && echo ^[pa >> locked_users.txt^[j`

对下一行执行宏操作，输入 <kbd>@</kbd><kbd>B</kbd> 即可；后面三个类似的文本行，则可以用 <kbd>3</kbd><kbd>@</kbd><kbd>B</kbd> 轻松实现批量修改。



### 2.4. 对电话号码作格式化处理

接下来，创建一个 `Vim` 宏并存入寄存器 `"p`，实现将如下所示的电话号码：

`2798265253`

统一转换为符合美国人书写习惯的格式：

`(279) 826-5253`

其中一种参考方案实现如下：

- 将光标定位到 `2798265253` 这一行（即待批量处理的第一行）；
- 按 <kbd>Q</kbd><kbd>P</kbd> 启动宏录制，并将其存入寄存器 `"p`；
- 按 <kbd>Shift</kbd><kbd>I</kbd> 从行首进入插入模式；
- 输入左小括号 `(`，并按 <kbd>Escape</kbd> 回到正常模式；
- 键入三次 <kbd>L</kbd>，让光标定位到 `9` 处；
- 按 <kbd>A</kbd> 在光标后添加文字，输入 <kbd>)</kbd><kbd>Space</kbd> 后，按 <kbd>Escape</kbd> 返回正常模式。
- 按三次 <kbd>L</kbd> 将光标移至 `6` 的下方；
- 按 <kbd>A</kbd><kbd>-</kbd> 插入一个连字符，再按 <kbd>Escape</kbd> 回到正常模式；
- 按 <kbd>J</kbd> 将光标下移一行，以便快速重复宏操作；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"p` 中的录制内容，可输入命令 `:reg p` + <kbd>Enter</kbd>。内容如下：

`"p  I(^[llla) ^[llla-^[j`

鉴于要处理的电话号码很多，文本行超出了屏幕，难以轻易获知需要重置执行多少次宏；此外，单纯使用 `@@` 来重复执行也很费时间。此时应该使用指定具体范围来应用宏操作。先用 `:set nu` 开启行号，再将光标定位到第 25 行；然后按 <kbd>Ctrl</kbd> + <kbd>F</kbd> 向下翻页，确定最后一个电话号码的行号为 73。

接着输入 `:25,73 normal @p` + <kbd>Enter</kbd>，通过 `normal` 命令指定具体范围并批量运行宏操作。之后再通过 <kbd>Ctrl</kbd> + <kbd>B</kbd> 上翻查看宏的执行情况。



### 2.5. 从日志文件中提取重要数据

下一组练习取材自 `Linux` 服务器的系统日志。这些内容是本地 `Linux` 防火墙阻止连接请求的日志记录。我们的目标是分别提取出时间戳、尝试连接的源 IP 地址以及目标端口。

其中，`SRC=` 字样后的内容即为源 IP 地址，例如：`SRC=190.18.193.152`。

目标端口则位于 `DPT=` 字样后，例如：`DPT=23`。

也就是利用 `Vim` 宏（假设录制到寄存器 `"l`）将下面这样的日志内容：

```markdown
Jan 13 09:57:01 www1 kernel: [3947771.808744] [BLOCK] IN=eth0 OUT= MAC=e6:e9:2d:04:b6:95:3c:8a:b0:0d:6f:f0:08:00 SRC=190.18.193.152 DST=2.5.9.1 LEN=40 TOS=0x02 PREC=0x00 TTL=51 ID=25120 PROTO=TCP SPT=12502 DPT=23 WINDOW=4078 RES=0x00 SYN URGP=0
```

批量精简为如下版本，并以逗号分隔：

```markdown
Jan 13 09:57:01,190.188.193.152,23
```

其中一种参考方案实现如下：

- 将光标定位到以 `Jan 13 09:57:01` 开头的这一行；
- 按 <kbd>Q</kbd><kbd>L</kbd> 启动宏录制，并将其存入寄存器 `"l`；
- 按 <kbd>0</kbd> 对光标作标准化处理，统一定位到行首；
- 按 <kbd>T</kbd><kbd>W</kbd> 将光标定位到时间戳后面的空格为止；
- 输入 `dtS` 删除当前光标到 `SRC=` 之间的所有内容；
- 按 <kbd>D</kbd><kbd>W</kbd> 删除 `SRC`；
- 按 <kbd>R</kbd><kbd>,</kbd> 将 `=` 替换为逗号 `,`；
- 按 <kbd>F</kbd><kbd>Space</kbd> 将光标定位到 IP 地址后的空格处；
- 输入 `d/DPT` + <kbd>Enter</kbd> 删除当前光标与 `DPT=` 之间的文字内容；
- 按 <kbd>D</kbd><kbd>W</kbd> 删除 `DPT`；
- 按 <kbd>R</kbd><kbd>,</kbd> 再将 `=` 替换为逗号 `,`；
- 按 <kbd>F</kbd><kbd>Space</kbd> 将光标定位到端口号后面的空格处；
- 按 <kbd>Shift</kbd><kbd>D</kbd> 删除这一行当前光标及其后面的剩余内容；
- 按 <kbd>J</kbd> 将光标下移一行，以便快速重复宏操作；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"l` 中的录制内容，可输入命令 `:reg l` + <kbd>Enter</kbd>。内容如下：

`"l   0twdtSdwr,f d/DPT^Mdwr,f Dj`

同样，还有其他方式可以实现上述任务。例如，要将 `SRC=` 改为 `,`，除了用上面的 <kbd>D</kbd><kbd>W</kbd><kbd>R</kbd> 实现，还可以使用 <kbd>2</kbd><kbd>C</kbd><kbd>W</kbd>。不妨停下来思考一下类似的备选方案对录制的宏进行修改，看看能否达到同样的效果。

若要对下一行日志执行录制的宏，输入 <kbd>@</kbd><kbd>L</kbd> 即可。如果没问题，就用 <kbd>@</kbd><kbd>@</kbd> 重复执行，直至处理完剩下的日志内容。



### 2.6. 将多行数据压缩为一行

再次强调，宏录制的是一系列按键操作。尽管我们一直在单行内容上练习宏的相关操作，宏也可以作用于多行。假如需要将下列三行通过录制的宏（假设存入寄存器 `"c`）按要求处理为一行，即从之前的：

```markdown
Country China
1,380,950,000 people

```

处理为：

```markdown
1,380,950,000;China
```

其中一种参考方案实现如下：

- 将光标定位到以 `Country China` 开头的这一行；
- 按 <kbd>Q</kbd><kbd>C</kbd> 启动宏录制，并将其存入寄存器 `"c`；
- 按 <kbd>0</kbd> 对光标作标准化处理，统一定位到行首；
- 按 <kbd>D</kbd><kbd>W</kbd> 删除单词 `Country`；
- 按 <kbd>J</kbd> 将光标下移一行；
- 按 <kbd>D</kbd><kbd>Shift</kbd><kbd>W</kbd> 将数字存入未命名寄存器（unnamed register）；
- 按 <kbd>K</kbd> 上移光标到刚才那行；
- 按 <kbd>Shift</kbd><kbd>P</kbd> 将数字粘贴到光标位置的前方；
- 按 <kbd>R</kbd><kbd>;</kbd> 将空格替换为分号；
- 按 <kbd>J</kbd> 将光标下移一行；
- 按 <kbd>2</kbd><kbd>D</kbd><kbd>D</kbd> 删除当前行与下一行内容；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"c` 中的录制内容，可输入命令 `:reg c` + <kbd>Enter</kbd>。内容如下：

`"c  0dwjdWkPr;j2dd`

接着，可以通过引入数量词，即 <kbd>4</kbd><kbd>@</kbd><kbd>C</kbd>，将上述宏操作再重复执行四次，实现该组数据的批量处理。

同样，要在 `Vim` 中实现上述效果还有很多其他方案可供选择。



### 2.7. 从 HTML 中提取数据

下列这行文本为一组 `HTML` 链接列表（即 `<a>` 标签）：

```html
<a href="#">@armyspy.com</a><a href="#">@cuvox.de</a><a href="#">@dayrep.com</a><a href="#">@einrot.com</a><a href="#">@fleckens.hu</a><a href="#">@gustr.com</a><a href="#">@jourrapide.com</a><a href="#">@rhyta.com</a><a href="#">@superrito.com</a><a href="#">@teleworm.us</a>
```

最终需要通过 `Vim` 宏（假设存入寄存器 `"q`）处理成下列效果：

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

其中一种参考方案实现如下：

- 将光标定位到以 `<a` 开头的文本行；
- 按 <kbd>Q</kbd><kbd>Q</kbd> 启动宏录制，并将其存入寄存器 `"q`；
- 按 <kbd>D</kbd><kbd>F</kbd><kbd>@</kbd> 删除当前光标到 `@` 之间（包含 `@`）的所有内容；
- 按 <kbd>F</kbd><kbd><</kbd> 将光标定位到下一处 `<` 位置；
- 按 <kbd>C</kbd><kbd>F</kbd><kbd>></kbd> + <kbd>Enter</kbd> + <kbd>Escape</kbd>，将 `</a>` 替换为一个换行标记；
- 最后，按 <kbd>Q</kbd> 停止宏录制。

要查看寄存器 `"q` 中的录制内容，可输入命令 `:reg q` + <kbd>Enter</kbd>。内容如下：

`"q  df@f<cf>^M^[`

输入 <kbd>@</kbd><kbd>Q</kbd> 即可运行这个宏。继续重复执行，按 <kbd>@</kbd><kbd>@</kbd> 即可，直至处理完其余链接内容。



## 3 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-09-Macros.pdf`



