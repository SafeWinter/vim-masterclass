# L43 Exercise 12 - Vim Buffers
---

## 1 训练目标

练习 `Vim` 对多个缓冲区的各类操作。[^1]



## 2 操作指令

### 2.1. 打开 buf* 文件

用 `Vim` 打开源码包内所有以 `buf` 开头的练习文件（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim buf*
```



### 2.2. 查看缓冲区 View the buffers

使用命令 `:buffers` 或 `:files` 亦或是 `:ls` 来查看缓冲区列表，三者效果都一样。运行后将看到如下信息：

```markdown
:ls
  1 %a   "buf-ant.txt"                  line 1
  2      "buf-bed.txt"                  line 0
  3      "buf-cat.txt"                  line 0
  4      "buf-dad.txt"                  line 0
```



### 2.3. 切换缓冲区 Switch buffers

`:buffer` 命令，或简写为 `:b`，可用于切换缓冲区。试通过与文件 `buf-bed.txt` 关联的唯一缓冲区编号来打开该缓冲区；即输入 `:b` + <kbd>Enter</kbd>。

接着，再用文件名切换到与文件 `buf-cat.txt` 关联的缓冲区。具体做法是输入命令 `:b buf-cat.txt` + <kbd>Enter</kbd>。

接着，再练习用 <kbd>Tab</kbd> 键补全功能打开与文件 `buf-dad.txt` 关联的缓冲区，即输入命令 `:b` + <kbd>Space</kbd> + <kbd>Tab</kbd> + <kbd>Tab</kbd> + <kbd>Tab</kbd> + <kbd>Tab</kbd> + <kbd>Enter</kbd>。

想要快速返回刚才打开的缓冲区，按 <kbd>Ctrl</kbd> + <kbd>^</kbd> 即可 [^2]。此时窗口中应该看到 `buf-cat.txt` 中的内容。

用 `:ls` + <kbd>Enter</kbd> 查看缓冲区列表，注意观察上面的标记符号。3 号缓冲区被标记为 `%a`，表示该缓冲区是当前窗口显示的活动缓冲区；4 号缓冲区的标记为 `#`，表示一个备用缓冲区（alternative buffer）。

```markdown
:ls
  1      "buf-ant.txt"                  line 1
  2      "buf-bed.txt"                  line 1
  3 %a   "buf-cat.txt"                  line 0
  4 #    "buf-dad.txt"                  line 1
```

再按 <kbd>Ctrl</kbd> + <kbd>^</kbd> 切回 4 号缓冲区。

执行命令 `:bprevious` + <kbd>Enter</kbd> 来到 3 号缓冲区。您也可以使用简写形式 `:bp` + <kbd>Enter</kbd> 实现该操作。

接着，输入 `:bp` + <kbd>Enter</kbd> 切到上一个缓冲区，即 2 号缓冲区。

现在调转方向，用 `:bnext` + <kbd>Enter</kbd> 命令或其简写形式 `:bn` + <kbd>Enter</kbd> 来到下一个缓冲区，即 3 号缓冲区。

要快速转到列表中的第一个缓冲区，执行命令 `:bfirst` 即可。当然也可以使用它的简写形式 `:bf` + <kbd>Enter</kbd> 来实现同样的效果。

要换到列表中的最后一个缓冲区，使用命令 `:blast` + <kbd>Enter</kbd> 或 `:bl` + <kbd>Enter</kbd> 即可。



### 2.4. 同时编辑多个缓冲区 Edit multiple buffers at once

对当前缓冲区的内容进行更改。例如键入 <kbd>I</kbd> 启用插入模式，然后输入一些文字（例如 `dad`），并按 <kbd>Escape</kbd> 键回到正常模式。

在尝试使用命令 `:b2` 切到 2 号缓冲区。若此时没有启用 `hidden` 选项，`Vim` 将提示如下报错信息：

```markdown
E37: No write since last change (add ! to override)
```

根据提示输入 `:b!2` + <kbd>Enter</kbd>，这样就强制打开了 2 号缓冲区。再用 `:ls` + <kbd>Enter</kbd> 查看缓冲区列表，会看到之前的缓冲区新增了 `h` 和 `+` 标记，说明该缓冲区是一个修改过的隐藏缓冲区。

```markdown
:ls
  1      "buf-ant.txt"                  line 1
  2 %a   "buf-bed.txt"                  line 1
  3      "buf-cat.txt"                  line 0
  4 #h + "buf-dad.txt"                  line 1
```

现在启用 `hidden` 选项，输入命令 `:set hidden` + <kbd>Enter</kbd>。再修改当前缓冲区的内容，例如按 <kbd>I</kbd> 开启插入模式，输入 `bed` 后按 <kbd>Escape</kbd> 键返回正常模式。

再用 `:b1` + <kbd>Enter</kbd> 切到 1 号缓冲区，此时不会出现任何报错信息。用 `:ls` + <kbd>Enter</kbd> 进行查看，会发现 2 号和 4 号都被打上了 `h` 和 `+` 标记，说明它们都是修改过的隐藏缓冲区：

```markdown
:ls
  1 %a   "buf-ant.txt"                  line 1
  2 #h + "buf-bed.txt"                  line 1
  3      "buf-cat.txt"                  line 0
  4  h + "buf-dad.txt"                  line 1
```



### 2.5. 缓冲区的增删操作 Add and delete buffers

练习再打开一个名为 `nav.txt` 的文件进行编辑。具体做法是输入 `:e nav.txt` + <kbd>Enter</kbd>。这样 `nav.txt` 的内容就被加载到了当前窗口显示的缓存区中。再用 `:ls` + <kbd>Enter</kbd> 进行查看，将得到如下结果：

```markdown
:ls
  1 #h   "buf-ant.txt"                  line 1
  2  h + "buf-bed.txt"                  line 1
  3      "buf-cat.txt"                  line 1
  4  h + "buf-dad.txt"                  line 1
  5 %a   "nav.txt"                      line 1
```

假定此时无需编辑 `nav.txt` 文件，则可以输入 `:bd` + <kbd>Enter</kbd> 进行删除。再用 `:ls` + <kbd>Enter</kbd> 查看缓冲区列表，可以看到如下结果：

```markdown
:ls
  1 %a   "buf-ant.txt"                  line 1
  2  h + "buf-bed.txt"                  line 1
  3      "buf-cat.txt"                  line 1
  4  h + "buf-dad.txt"                  line 1
```

接着，输入 `:bd3` + <kbd>Enter</kbd> 删除 3 号缓冲区。再用 `:ls` + <kbd>Enter</kbd> 查看缓冲区列表，会可以看到如下结果：

```markdown
:ls
  1 %a   "buf-ant.txt"                  line 1
  2  h + "buf-bed.txt"                  line 1
  4  h + "buf-dad.txt"                  line 1
```



### 2.6. 练习 Vim 内置资源管理器的用法 Use the Explorer

下面尝试用 `Vim` 内置的资源管理器再打开一个名为 `help.txt` 的文件。具体做法：输入 `:E` + <kbd>Enter</kbd> 启动资源管理器，然后使用学过的 `Vim` 导航命令将光标定位到 `help.txt` 文件下，并按 <kbd>Enter</kbd> 键将其加载到当前窗口内。

然后，输入 `:bd` + <kbd>Enter</kbd> 舍弃（discard）该缓冲区。



### 2.7. 对所有缓冲区批量执行命令 Execute a command in all buffers

下面练习对所有缓冲区执行全局替换操作。回忆一下替换命令的语法：`:[range]s[ubstitute]/{pattern}/{string}/[flags]`；再回忆一下选中整个文件范围的 `%` 标记，以及可用于执行全局替换的标记 `g`。这样一来，对应的全局替换命令就可以写作：`:%s/{old}/{new}/g`。然后将其与 `:bufdo` 命令相结合，实现将每个缓冲区内的字符 `#` 批量替换为字符 `@`。

具体做法：输入命令 ` :bufdo %s/#/@/g` + <kbd>Enter</kbd>。用 `:ls` + <kbd>Enter</kbd> 进行检查，会看到这些缓冲区都被修改了，都打上了 `+` 标记。在输入 `:bf` + <kbd>Enter</kbd> 来到第一个缓冲区，看看是否也替换成功了。得到的结果如下所示：

```markdown
   @     @     @  @@@@@@@
  @ @    @@    @     @
 @   @   @ @   @     @
@     @  @  @  @     @
@@@@@@@  @   @ @     @
@     @  @    @@     @
@     @  @     @     @
This training is provided by LinuxTrainingAcademy.com.
```



### 2.8. 放弃所有缓冲区中的变更内容 Abandon your changes to all buffers

如果编辑好了 `vimrc` 文件，就可以保存内容并退出 `Vim`，使用命令：`:wq!` + <kbd>Enter</kbd>。

如果希望后续能继续练习上述操作，则可以使用命令 `:qall!` + <kbd>Enter</kbd> 放弃所有修改；否则可以用 `:wall` 命令来保存所有内容。





---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-12-Buffers.pdf`

[^2]: 经验证，为避免与 `Windows Terminal` 快捷键冲突，应使用 <kbd>Ctrl</kbd> + <kbd>6</kbd>；另外，该组合键在 `Linux` 系统下仍然有效。



