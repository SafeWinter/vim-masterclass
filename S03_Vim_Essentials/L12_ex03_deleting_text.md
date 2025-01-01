# L12 Exercise 03 - Deleting Text
---

## 1 训练目标

在文件中删除文本。同时熟悉 `[count]{motion}` 模式。[^1]



## 2 训练指引

依次按下列指令完成操作：

### 2.1 打开文件 practicedeleting.txt

打开一个命令行会话，并使用 Vim 打开随堂源码包中的文件 `practicedeleting.txt`（假设压缩文件已解压到本地 `Download` 文件夹）：

```bash
cd Downloads
cd vimclass
vim practicedeleting.txt
```



### 2.2 练习删除单个字符

光标移至第三行，方式各异：既可以连续按 <kbd>J</kbd>，也可以使用 <kbd>3</kbd><kbd>G</kbd><kbd>G</kbd>、<kbd>3</kbd><kbd>Shift</kbd><kbd>G</kbd>，甚至是命令模式下执行 `:3` + <kbd>Enter</kbd>。

光标定位到错误单词 `mistakke` 多出的任意一个 `k`，敲 <kbd>X</kbd> 键进行删除。删除前的句子如下所示：

```markdown
First, fix this spelling mistakke.
```

删除后：

```markdown
First, fix this spelling mistake.
```

再将光标移至第四行，依次删除单词中重复的字母，通过敲 <kbd>X</kbd> 键删除光标所在字符实现。操作前的句子如下所示：

```markdown
Fixx theese allso.
```

依次删除多出的 `x`、`e`、`l` 后，该句变为：

```
Fix these also.
```

再将光标移至下一行：

```markdown
Delete this text with the X command.
```

将光标定位到该行末尾：要么重复按下 <kbd>L</kbd> 键，要么使用 <kbd>$</kbd> 键。此时用大写的 <kbd>X</kbd> 键删除所有文本，却唯独剩下末尾的句点没删完：

```markdown
.
```

按下 <kbd>X</kbd> 键删除剩余的那个字符，于是该行被清空。



### 2.3 练习 motion：删除（Practice deleting motions）

光标移至下一行：

```markdown
Who let the dogs out? cats
```

将光标定位到紧挨问号右边的那个字符、即 `?` 与 `cats` 之间的空格处。删除该行剩余文本。可以用 `d$`，或者更短的 **D** 命令。效果如下：

```markdown
Who let the dogs out?
```

再将光标移至第 43 行（提示：`43gg`），用 `d` 操作符删除第一个单词。回忆基本形式 `count{motion}`，使用 `dw` 或 `dW` 完成任务。首个单词删除前：

```markdown
Far far away, behind the wild mountains, far from the countries Vokalia and
```

首个单词删除后：

```markdown
far away, behind the wild mountains, far from the countries Vokalia and
```

再删除第二个单词，该行变为：

```markdown
away, behind the wild mountains, far from the countries Vokalia and
```

再使用两个按键，删除文本 `away, `。回忆一下，移动命令 `w` 会停在标点符号处，而大写的 `W` 则会忽略标点，将光标停在其他空白处。因此通过两次按键来删除 `away` 要使用 `dW`。结果如下：

```markdown
behind the wild mountains, far from the countries Vokalia and
```

再将光标移至第一个单词 `the` 的起始位置。使用一个操作与一次移动来删除句子中的第一个单词。要实现该目标，需键入 `db`；另外也可以用 `dB`，结果如下：

```markdown
the wild mountains, far from the countries Vokalia and
```

接着，删除单词 `the wild `。提示一种方法：使用 <kbd>2</kbd><kbd>D</kbd><kbd>W</kbd>。

```markdown
mountains, far from the countries Vokalia and
```

然后再删除 `mountains, far `。刚好划过这段内容的一个 `motion` 命令为 `2W`，因此使用 `d2W` 完成文本删除。剩余内容如下：

```markdown
from the countries Vokalia and
```



### 2.4 文本行的删除练习（Practice deleting lines）

使用 `dd` 删除一行。此时光标定位到以下这行：

```markdown
Consonantia, there live the blind texts. Separated they live in Bookmarksgrove
```

要删除多行，使用 `[count]dd`。比如删除以下这些行：

```markdown
Consonantia, there live the blind texts. Separated they live in Bookmarksgrove
right at the coast of the Semantics, a large language ocean.

```

仔细观察，此时有三行要删除：第一行以 `Consonantia` 开头，下一行以 `right`，第三行是空白行，根本没有文本。要删除这三行，使用 `3dd`。之后光标位于这句上：

```markdown
A small river named Duden flows by their place and supplies it with the
```

若要通过一次敲击再删除下一个三行，只需键入一个句点键 <kbd>.</kbd>，上一次命令操作就会被重复执行。按下 <kbd>.</kbd> 键后，下面三行将被删除：

```markdown
A small river named Duden flows by their place and supplies it with the
necessary regelialia. It is a paradisematic country, in which roasted parts of
sentences fly into your mouth.
```



### 2.5 保存变更内容（或不保存）Save your work (or not!)

若要保存变更内容并让 Vim 继续运行，可使用 `:w` + <kbd>Enter</kbd>；保存变更并立即退出，则键入 `:wq` + <kbd>Enter</kbd> 即可；若退出时放弃更改文件，则使用 `:q!` + <kbd>Enter</kbd>。三种方式由您自行决定。



### 2.6 自由练习

完成上述练习后，按你自己的想法练习文件内容的删除。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-03-DeletingText.pdf`