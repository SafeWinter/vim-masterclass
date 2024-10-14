# L21 Inserting, Changing, Replacing, and Joining
---

演示文件：`vimclass/inserting.txt`

本节介绍文本的插入、变更、替换，以及文本行的合并。



## 1 定位到行首非空字符，并启用插入模式

按 <kbd>I</kbd>：相当于 <kbd>^</kbd> + <kbd>I</kbd>



## 2 在紧挨光标的下一个字符位置启动插入模式

按 <kbd>A</kbd>



## 3 定位到一行末尾，并启用插入模式

按 <kbd>Shift</kbd> + <kbd>A</kbd>：表示 ***A**ppend to the end of the line*



## 4 定位到光标的下一行，并启用插入模式

按 <kbd>O</kbd>

若要定位到上一行并启用插入模式，则使用 <kbd>Shift</kbd> + <kbd>O</kbd>



## 5 快速输入 80 个星号符

<kbd>8</kbd><kbd>0</kbd><kbd>I</kbd><kbd>*</kbd> + <kbd>Esc</kbd>



## 6 在光标下方创建五行已 # 开头的行

<kbd>5</kbd><kbd>O</kbd><kbd>#</kbd> + <kbd>Esc</kbd>

适用场景：快速注释配置文件或 `Shell` 脚本。



## 7 在光标下方创建四行以 IP 片段 10.11.12. 开头的行

<kbd>4</kbd><kbd>O</kbd> + <kbd>10.11.12.</kbd> + <kbd>Esc</kbd>

实测效果：

![](../../masterJsFp2/assets/21-1.png)



## 8 使用替换模式

开启方式：<kbd>Shift</kbd> + <kbd>R</kbd>（按 <kbd>Esc</kbd> 返回常规模式）

注意：若 **只有一个字符** 需要替换，则使用小写的 <kbd>R</kbd> 即可，替换完毕将自动返回常规模式。



## 9 变更一个单词

使用 `c` 命令（表 **c**hange），格式为：`["x]c{motion}`



### 9.1 将 canine 快速替换为 cat

方法：光标定位到字母 `c`，按 <kbd>C</kbd><kbd>W</kbd> + `cat` + <kbd>Esc</kbd>

发散：将 canine 同时存入寄存器 `"a`：输入 <kbd>"</kbd><kbd>A</kbd> + <kbd>C</kbd><kbd>W</kbd> + `cat` + <kbd>Esc</kbd>



### 9.2 将光标及后面的内容都删掉，并快速替换为其他内容

例如将 `car` 及后面的内容都替换为 `mouse`：光标先定位到字母 `c`，然后按 <kbd>C</kbd><kbd>$</kbd> + `mouse` + <kbd>Esc</kbd>

类比 `d` 命令，<kbd>C</kbd><kbd>$</kbd> 也可以等效使用 <kbd>Shift</kbd> + <kbd>C</kbd>



### 9.3 变更一整行内容

使用 <kbd>C</kbd><kbd>C</kbd>（联想 <kbd>D</kbd><kbd>D</kbd>）



## 10 快速切换大小写

使用 <kbd>~</kbd>：将光标处的单个字母从小写变为大写，或从大写变为小写。

切换当前单词的大小写：按 <kbd>G</kbd><kbd>~</kbd><kbd>W</kbd>（语法：`g~{motion}`）

切换当前行所有字符的大小写，方法为：

1. 光标定位到行首；
2. 按 <kbd>G</kbd><kbd>~</kbd><kbd>$</kbd>。

类比 `d` 命令和 `c` 命令，这里的 <kbd>G</kbd><kbd>~</kbd><kbd>$</kbd> 也等效于 <kbd>G</kbd><kbd>~</kbd><kbd>~</kbd>



## 11 将文字转为大写

语法格式：`gU{motion}`（`U` 即 `Upper` 的首字母）

例如，将当前单词转为大写：<kbd>G</kbd> + （<kbd>Shift</kbd> + <kbd>U</kbd>）+ <kbd>W</kbd>

将整行内容大写：使用命令 `gUU`（两个 `U` 都是大写形式）



## 12 将文字转为小写

语法格式：`gu{motion}`（大写为 `U`，小写自然为 `u`）

将整行内容小写：使用命令 `guu`（两个 `u` 都是小写形式）



## 13 合并多行

使用 <kbd>Shift</kbd> + <kbd>J</kbd>：用于合并光标所在行及下一行，并智能补足一个或两个空格。

关于合并后 Vim 的智能空格补足机制：

| 首行的末尾 | Vim 补充空格数 |
| :--------: | :------------: |
|  既没有 `.`、又没有空格  | 1 |
| 以 `.` 结尾 | 2 |
| 以 `.<Space>` 结尾 | 1 |
| 以 `.<Space><Space>` 结尾（即自带两个及以上空格） | 0 |

如果不希望 Vim 自动补空格，使用 `gJ` 命令。

合并包含光标在内的余下三行：<kbd>3</kbd> +（<kbd>Shift</kbd> + <kbd>J</kbd>）（即 `3J` 命令）
