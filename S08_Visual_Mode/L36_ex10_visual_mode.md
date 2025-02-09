# L36 Exercise 10 - Visual Mode
---

## 1 训练目标

熟悉 `Vim` 可视化模式的各种用法。[^1]



## 2 操作指令

### 2.1. 打开 visual-practice.txt 文件

用 `Vim` 打开源码包内的练习文件 `visual-practice.txt`（默认解压到 `Downloads` 文件夹下）：

```bash
cd Downloads
cd vimclass
vim visual-practice.txt
```



### 2.2. 字符级可视化模式练习 Characterwise Visual Mode

试将 `=>` 与 `<=` 之间的文字内容用字符级视觉模式删除。这是删除前的原始版本：

```markdown
Use characterwise visual mode to delete this => DELETE ME, DELETE ME, Yes!!! <=
```

删除后变为：

```markdown
Use characterwise visual mode to delete this =><=
```

具体实现：先将光标定位到单词 `DELETE` 前的空格位置，例如使用 `tD` 实现。然后键入 <kbd>V</kbd> 进入字符级可视化模式，并通过输入 <kbd>L</kbd>、或者 <kbd>W</kbd>、或者使用正向查找 <kbd>/</kbd> 定位到 `<` 之前的字符，具体方式自行确定，只要不选中 `<` 即可。最后键入 <kbd>D</kbd> 实现文字删除。

下一个练习，要求将第 3 行的句子 `Yank this sentence.` 存入未命名寄存器。注意不要包含该句后面的空格。具体实现：先将光标定位到这句话的任意位置（例如输入 <kbd>J</kbd><kbd>J</kbd><kbd>0</kbd> 将光标定位到该句开头）；然后键入 <kbd>Y</kbd><kbd>I</kbd><kbd>S</kbd> 实现复制。这里的 `yis` 表示仅复制句子内容本身。

要查看未命名寄存器中的内容，可输入命令 `:reg "` + <kbd>Enter</kbd>。内容如下：

`""   Yank this sentence.`



### 2.3. 文本行可视化模式练习 Linewise Visual Mode

试将下列文字通过 `Vim` 的行级可视化模式合并为一行：

```markdown
This entire paragraph should be on the same line.
But it isn't!
I don't know who typed this, but they didn't do a
very
good
job.
Did they?
```

最终效果：

```markdown
This entire paragraph should be on the same line.  But it isn't!  I don't know who typed this, but they didn't do a very good job.  Did they?
```

（注意：只要显示器不够大，一行文字就很可能会折行。此时可以通过 `:set nu` + <kbd>Enter</kbd> 命令显示行号来判定这段文本是否属于同一行）

为此，需要先将光标定位到如下所示的第一行的任意位置：

```markdown
This entire paragraph should be on the same line.
```

然后输入 <kbd>Shift</kbd><kbd>V</kbd> 进入行级可视化模式；键入 <kbd>I</kbd><kbd>P</kbd> 选中整个段落，这里的 `ip` 表示 **内部段落（inner paragraph）**。最后，输入 <kbd>Shift</kbd><kbd>J</kbd> 完成文本连接操作。

下一个练习，需要利用 `Vim` 的可视化模式将下列文字内容居中排列：

```markdown
##############################################################################
Header
Description
##############################################################################
```

使其变为以下效果：

```markdown
##############################################################################
                                    HEADER
                                 DESCRIPTION
##############################################################################
```

实现方法：先将光标定位到 `Header` 这一行，然后按 <kbd>Shift</kbd><kbd>V</kbd> 启用行级可视化模式；键入 <kbd>J</kbd> 让光标下移一行，并输入 <kbd>Shift</kbd><kbd>U</kbd> 将选中内容全部转为大写；再按 <kbd>G</kbd><kbd>V</kbd> 重新选中这些文本行，输入命令 `:center` + <kbd>Enter</kbd> 实现文字居中。



### 2.4. 区块级可视化模式练习 Blockwise Visual Mode

试用 `Vim` 的区块级可视化模式，对如下文字进行批量操作：

```markdown
Rank,Item
"001","Q-Tips"
"002","Paper Towels"
"003","Toilet Paper"
"004","Liquid Detergent"
"005","Mouthwash"
"006","Cereal"
"007","Bottled Water"
```

使其最终变为：

```markdown
Rank,Item
1,"Q-Tips"
2,"Paper Towels"
3,"Toilet Paper"
4,"Liquid Detergent"
5,"Mouthwash"
6,"Cereal"
7,"Bottled Water"
```

为此，先将光标定位到如下这行的开头位置：

```markdown
"001","Q-Tips"
```

接着输入 <kbd>Ctrl</kbd><kbd>V</kbd> 启用块级可视化模式 [^2]。键入 <kbd>L</kbd> 选中开头两列，然后下移光标到 `"007","Bottled Water"` 这行（具体可通过按六次 <kbd>J</kbd> 键实现）；接着按 <kbd>D</kbd> 或 <kbd>X</kbd> 删除高亮选中的文本。此时 `Vim` 回到正常模式（normal mode）。

按 <kbd>L</kbd> 将光标右移一列，并输入 <kbd>Ctrl</kbd><kbd>V</kbd> 再次进入块级可视化模式；再次键入六次 <kbd>J</kbd> 键将光标下移至 `7","Bottled Water"` 这行，按 <kbd>D</kbd> 或 <kbd>X</kbd> 键完成删除操作。

下一个练习，要求用块级可视化模式，在下列每行文字的开头插入 `# ` 字样。

改动前的原始版本如下：

```markdown
This is a comment.
So is this.
Why, this is also a comment.
Please, comment us out!
```

改动后要变为：

```markdown
# This is a comment.
# So is this.
# Why, this is also a comment.
# Please, comment us out!
```

为此，先将光标定位到 `This is a comment.` 这行的 `T` 字符上，并按 <kbd>Ctrl</kbd><kbd>V</kbd> 进入块级可视化模式；接着输入 <kbd>J</kbd><kbd>J</kbd><kbd>J</kbd> 高亮选中后三行的首字符。最后通过输入 <kbd>Shift</kbd><kbd>I</kbd> + <kbd>#</kbd><kbd>Space</kbd> + <kbd>Escape</kbd>，完成 `# ` 字样的插入。

接着，在改好的文字基础上，在实现另一个练习效果。也就是将刚才的操作结果：

```markdown
# This is a comment.
# So is this.
# Why, this is also a comment.
# Please, comment us out!
```

再改为下列版本：

```markdown
" This is a comment.
" So is this.
" Why, this is also a comment.
" Please, comment us out!
```

注意：双引号标记的内容在 `vimrc` 文件中代表注释信息。

按 <kbd>G</kbd><kbd>V</kbd> 快速重新选中刚才的高亮区域，再按 <kbd>C</kbd><kbd>"</kbd> + <kbd>Escape</kbd> 将 `#` 批量改为 `"`。

最后一个练习项目，需要再用 `Vim` 的块级可视化模式，在如下内容的每行末尾分别添加 `# EOL` 字样：

```markdown
>
>>>
>>>>>
>>>>>>>
>>>>>>>>>>
>>>>>>>
>>>>>
>>>>
>
```

使其最终变为：

```markdown
> # EOL
>>> # EOL
>>>>> # EOL
>>>>>>> # EOL
>>>>>>>>>> # EOL
>>>>>>> # EOL
>>>>> # EOL
>>>> # EOL
> # EOL
```

为此，先将光标定位到文本区首行首列（可通过 `27gg` 实现）；然后按 <kbd>Ctrl</kbd><kbd>V</kbd> 开启块级可视化模式，并按八次 <kbd>J</kbd> 键选中整个文本块的首列；接着键入 <kbd>$</kbd> 来选中各行其余文本。最后按 <kbd>Shift</kbd><kbd>A</kbd> 批量添加文字，输入 <kbd>Space</kbd> + `# EOL` + <kbd>Escape</kbd> 即可。



## 3 退出 Vim

若要放弃文件变更以便下次重新练习，使用退出命令 `:q!` + <kbd>Enter</kbd>。



---

[^1]: 本节练习另附精美排版 PDF 格式，阅读体验更佳，详见：`vimclass/Exercise-10-VisualMode.pdf`
[^2]: 为避免和系统内置的粘贴快捷键相冲突，对于 `Windows` 版本的 `Vim`，块级可视化模式通过 <kbd>Ctrl</kbd> + <kbd>Q</kbd> 开启；而在 `WSL` 环境下 `Ubuntu` 系统中的 `Vim`，则需要通过 <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>V</kbd> 来启动。

 
