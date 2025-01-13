# L26 Exercise 07 - Search, Find, and Replace
---



## 1 训练目标

练习 `Vim` 中的文本搜索、查找与替换。[^1]



## 2 操作指令

### 2.1. 打开 search-practice.txt 文件

用 `Vim` 打开源码包内的练习文件 `search-practice.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim search-practice.txt
```



### 2.2. 同一行内的搜索练习

以下为练习文件的第一行：

```markdown
The Time Traveller (for so it will be convenient to speak of him) was expounding
```

按 <kbd>F</kbd><kbd>F</kbd> 将光标定位到该行单词 `for` 的首字符 `f` 上；再次键入 <kbd>F</kbd><kbd>F</kbd> 将定位到下一个 `of` 的 `f` 字符位置。切记：在同一行重复该操作，按 <kbd>;</kbd> 即可。

接着，将光标重新定位到 `for` 的首字母。做法：按 <kbd>,</kbd> 实现反向重复检索。

然后，将光标置于单词 `Traveller` 的开头，键入 <kbd>Shift</kbd><kbd>F</kbd> + <kbd>Shift</kbd><kbd>T</kbd> 实现反向查找。

再将光标置于单词 `be` 的前一个字符位置，即空格上。做法：利用 `till` 命令，输入 <kbd>T</kbd><kbd>B</kbd> 即可。

将光标定位到单词 `speak` 的前一个字符（即空格）位置。做法：按 <kbd>T</kbd><kbd>S</kbd>。

最后，将光标定位到单词 `for` 后面的空格上。做法：按 <kbd>Shift</kbd><kbd>T</kbd> + <kbd>R</kbd>。



### 2.3. 当前文件内的搜索练习

查找所有的 `and `，并将光标定位到每个匹配项的开头位置至少一次。做法：键入 `/and` + <kbd>Space</kbd> + <kbd>Enter</kbd>（注意：若没有在 `and` 后添加空格，则单词 `incandescent` 也会视为匹配项）。接着用 <kbd>N</kbd> 重复上述操作，遍历当前文件中的所有匹配项。 

然后掉转搜索方向，并反复按 <kbd>Shift</kbd><kbd>N</kbd>，让光标依次定位到各匹配项的开头位置。

最后，反向检索关键词 `to`。具体做法：键入 <kbd>?</kbd><kbd>T</kbd><kbd>O</kbd>。再用 <kbd>N</kbd> 重复该操作直到反向检索一整圈；接着键入 <kbd>Shift</kbd><kbd>N</kbd> 掉转反向检索的顺序，直到再检索一整圈。



### 2.4. 单词搜索练习

将光标定位到文件中首次出现单词 `it` 的 `i` 字母下方。实现方法：键入 <kbd>G</kbd><kbd>G</kbd> 移至文件开头，然后按 <kbd>2</kbd><kbd>F</kbd><kbd>I</kbd> 直接定位到第二个 `i` 字母位置；然后输入 <kbd>\*</kbd>，光标将移动到下一处单词 `it` 位置。按 <kbd>N</kbd> 重复上述操作，直到光标重新回到文件第一行。

接下来练习 `Vim` 的反向检索。先将光标定位到第二行的单词 `us` 上，可以用 <kbd>J</kbd> 下移一行，并通过 <kbd>Shift</kbd><kbd>F</kbd><kbd>U</kbd> 反向检索字符 `u`。接着按下 <kbd>#</kbd> 键，就能将光标定位到文件最后一处 `us` 上。最后，通过按 <kbd>N</kbd>，直到将光标重新定位到出现在该文件第二行的 `us` 一词上。



### 2.5. 全局替换练习

将文中所有的 `sat` 替换为 `laid`。具体做法：先输入 `:%s/sat/laid/g` + <kbd>Enter</kbd>。切记：这里的 `%` 表示一个特殊范围，代表整个文件；而启用 `g` 标志主要是为了确保在同一行中出现的 `sat` 字样都能被替换为 `laid`。如果不确定某一行是否存在多个匹配项，则可以考虑用 `g` 标志来确保替换掉所有的匹配项。



## 3 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-07-SearchFindReplace.pdf`

