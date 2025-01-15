# L29 Exercise 08 - Text Objects
---



## 1 训练目标

熟悉 `Vim` 中的各类文本对象。[^1]



## 2 操作指令

### 2.1. 打开 textobjectspractice.txt 文件

用 `Vim` 打开源码包内的练习文件 `textobjectspractice.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim textobjectspractice.txt
```



### 2.2. 单词对象练习 Word Objects

将光标定位到首行单词 `Time` 的任意位置，例如按 <kbd>F</kbd><kbd>I</kbd> 定位到最近的 `i` 字符下。然后按 <kbd>D</kbd><kbd>A</kbd><kbd>W</kbd> 删除该单词。注意观察，此时整个单词都被删除了，与使用 <kbd>D</kbd><kbd>W</kbd> 删除的结果不同。

接下来再将单词 `Traveller` 改为 `tourist`。具体做法：用 <kbd>C</kbd><kbd>I</kbd><kbd>W</kbd> 更改内部单词（inner word），然后输入 `tourist`。最后按 <kbd>Escape</kbd> 键返回常规模式。



### 2.3. 区块对象 `( )` 练习 Block Object ( )

按 <kbd>W</kbd> 将光标移至左小括号位置，然后将括号内的文本改为 `as we will call him`。具体做法：按 <kbd>C</kbd><kbd>I</kbd><kbd>(</kbd> 或 <kbd>C</kbd><kbd>I</kbd><kbd>)</kbd> 变更该区块内的文字内容。注意观察，此时光标刚好位于小括号内，接着输入 `as we will call him`，再按 <kbd>Escape</kbd> 键返回常规模式。

 此时文档第一行如下所示：

```markdown
The tourist (as we will call him) was expounding.
```

再定位到如下文本行，并令光标处于小括号内部、或就在小括号上：

```markdown
print("The weatherman said, 'This weekend will be warm,' but that was a lie.")
```

这是其中一种实现方案：按 <kbd>/</kbd><kbd>(</kbd> + <kbd>Enter</kbd>。接着，试通过三个字符的组合命令删除小括号这一整块内容（即 `("The weatherman said, 'This weekend will be warm,' but that was a lie.")`）。该命令为 <kbd>D</kbd><kbd>A</kbd><kbd>(</kbd> 或者 <kbd>D</kbd><kbd>A</kbd><kbd>)</kbd>。



### 2.4. 引用字符串练习 Quoted Strings

光标移至下一行，并将其定位到双引号内的任意位置（例如使用 <kbd>/</kbd><kbd>"</kbd> + <kbd>Enter</kbd>）。然后将下列文字：

```markdown
print("The weatherman said, 'This weekend will be warm,' but that was a lie.")
```

改为：

```markdown
print("It was cold!")
```

具体做法：键入 <kbd>C</kbd><kbd>I</kbd><kbd>"</kbd>，并输入 `It was cold!`，再按 <kbd>Escape</kbd> 键返回常规模式。

接着移至下一行，这次需要将单引号内的文字由 `'This weekend will be warm,'` 改为 `'It is hot outside,'`。为此，先用 <kbd>/</kbd><kbd>'</kbd> + <kbd>Enter</kbd> 进行正向搜索，然后输入 <kbd>C</kbd><kbd>I</kbd><kbd>'</kbd>，并将原文本改为 `It is hot outside,`。最后按 <kbd>Escape</kbd> 键返回常规模式。



### 2.5. 区块对象 `[ ]` 练习 Block Object [ ]

快速删除下列括号内所有文字内容。这是删除前的原始文本：

```python
scripts=[ 'bin/backup',
          'bin/backup-all',
          'bin/backup-db-only',
          'bin/backup-files-only' ]
```

删除后将变为：

```python
scripts=[]
```

先将光标定位到括号内的任意位置，例如通过检索 `bin` 实现：执行命令 `/bin` + <kbd>Enter</kbd>。然后，按 <kbd>D</kbd><kbd>I</kbd><kbd>[</kbd> 或者 <kbd>D</kbd><kbd>I</kbd><kbd>]</kbd> 删除方括号内的所有内容。



### 2.6. 区块对象 `< >` 练习 Block Object < >

按 <kbd>J</kbd><kbd>J</kbd> 将光标移至如下这行：

```markdown
<yank_me>
```

接着，将尖括号内的文本复制到 `"i` 寄存器中。具体做法：输入 `"iyi>` 或者 `"iyi<`。然后查看寄存器 `"i` 中的内容是否为 `yank_me`，方法是：输入命令 `:reg i` + <kbd>Enter</kbd> 。

然后，再连同尖括号本身，将文本 `<yank_me>` 复制后存入寄存器 `"a`。具体做法：输入命令 `"aya<` 或 `"aya>`，并通过命令 `:reg a` + <kbd>Enter</kbd> 进行确认，看看寄存器中的内容是否为 `<yank_me>`。



### 2.7. 标签对象练习 Tag Objects

试将下列文本行中的 `Linux Training Academy` 改为 `LTA`。改动前的原始文本如下：

```html
<p><a href="https://linuxtrainingacademy.com">Linux Training Academy</a></p>
```

这是变更后的效果：

```html
<p><a href="https://linuxtrainingacademy.com">LTA</a></p>
```

注意观察，目标文本位于 HTML 标签 `<a>` 内部。为此，需要先将光标定位到 `<a>` 标签内，例如通过 <kbd>/</kbd><kbd>H</kbd> + <kbd>Enter</kbd> 实现。然后按 <kbd>C</kbd><kbd>I</kbd><kbd>T</kbd>，即在标签内变更内容（**c**hange **i**nside **t**ag），然后输入 `LTA` + <kbd>Escape</kbd>。

下一段练习文本是 XML 格式的，改动前如下所示：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<CATALOG>
  <CD>
    <TITLE>Jazz At Massey Hall</TITLE>
    <ARTIST>The Quintet</ARTIST>
  </CD>
  <CD>
    <TITLE>Blue Train</TITLE>
    <ARTIST>John Coltrane</ARTIST>
  </CD>
  <CD>
    <TITLE>Saxophone Colossus</TITLE>
    <ARTIST>Sonny Rollins</ARTIST>
  </CD>
</CATALOG>
```

试将 `CATALOG` 中标题为 `Jazz At Massey Hall` 的 CD 条目完整删除，改动后的效果如下所示：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<CATALOG>
  <CD>
    <TITLE>Blue Train</TITLE>
    <ARTIST>John Coltrane</ARTIST>
  </CD>
  <CD>
    <TITLE>Saxophone Colossus</TITLE>
    <ARTIST>Sonny Rollins</ARTIST>
  </CD>
</CATALOG>
```

要删除 `<CD>` 标签，需要先将光标定位到包含 `Jazz At Massey Hall` 的条目对应的 `<CD>` 或 `</CD>` 位置。接着输入 <kbd>D</kbd><kbd>A</kbd><kbd>T</kbd>，表示删除该标签（**d**elete **a** **t**ag）。注意：如果光标定位到其他地方，可能只会删除内部嵌套的标签 `<TITLE>` 或者 `<ARTIST>`，而不是题目要求的整个 `<CD>` 标签。



### 2.8. 区块对象 `{ }` 练习 Block Object { }

试对如下这段文字进行相关文本对象操作：

```python
musicians = {
  'Charlie Parker': 'alto sax',
  'John Coltrane': 'tenor sax',
  'Sonny Rollins': 'tenor sax'
}
```

使其最终变为：

```python
musicians = { }
```

具体做法：先将光标定位到 `{ }` 区块的任意位置，例如检索关键字 `alto`，键入命令 <kbd>/</kbd><kbd>A</kbd><kbd>L</kbd><kbd>T</kbd><kbd>O</kbd> + <kbd>Enter</kbd>。然后输入 <kbd>D</kbd><kbd>I</kbd><kbd>{</kbd> 或  <kbd>D</kbd><kbd>I</kbd><kbd>}</kbd> 删除该区块内的文本，此处光标应位于下列内容所示的右大括号 `}` 位置：

```markdown
musicians = {
}
```

按 <kbd>K</kbd> 令光标上移一行，然后按 <kbd>Shift</kbd><kbd>J</kbd> 合并这两行即可。



### 2.9. 句子对象练习 Sentence Objects

复制下列句子内容并存入寄存器 `"s` 中。将光标定位到这句话的任意位置：

```markdown
Praesent rutrum purus ultricies, dignissim massa id, elementum felis.
```

注意观察，这句话并不是真正意义上的句子。切记，`Vim` 关注的是文本对象的边界，而非边界内的文字内容。句子是通过是否由标点符号 `.`、`!` 或者 `?` 结尾判定的。后面可以紧跟一个行终止符（the end of a line）或者一个空格或制表符。 

按 <kbd>"</kbd><kbd>S</kbd><kbd>Y</kbd><kbd>A</kbd><kbd>S</kbd> 将这句文本复制到寄存器 `"s` 中，并通过命令 `:reg s` + <kbd>Enter</kbd> 进行确认。



### 2.10. 段落对象练习 Paragraph Objects

按 <kbd>D</kbd><kbd>A</kbd><kbd>P</kbd> 删除整个段落。



## 3 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-08-TextObjects.pdf`



