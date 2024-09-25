# L06 Exercise 01 Creating and Editing a New File with Vim
---



***NOTE: For easier to read instructions download the PDF resource attached to this lesson.***

## **Creating and Editing a New File with Vim**

### ***Goal:***

The goal of this exercise is to practice creating files and editing them in vim.  You'll also practice changing between the normal mode, insert mode, and command mode.  During this practice exercise you will create a new file with vim, insert some text into that file, and save it.

### ***Instructions:***

#### **Create a file**

First, start a command line session on your local machine.  Next, use vim to edit a new file named myday.txt.  To do that type, **vim myday.txt** at the command line and press `<ENTER>`.

```bash
$ vim myday.txt
```

#### **Enter insert mode**

You now have a new file opened and you're placed into normal mode.  Press lowercase **i** to enter the insert mode.

#### **Add some text to the file**

Next, start typing.  Write a few sentences about the beginning of your day.  If you make a mistake while you're typing, you can press the backspace key to correct any errors.

#### **Continue adding text to the file**

Continue adding text to the file by typing three things you're grateful for.  Once you're done typing, press Escape to enter normal mode.

#### **Save the file**

Next save your changes.  You should already be in normal mode, but if you're not sure you can also press the Escape key again to be sure you are in normal mode.  Next, type **`:wq<ENTER>`** to save the file and exit vim.

#### **Verify the file was saved**

You can verify that you've saved your changes by looking at the contents of the file.  One way to do that is to use the vim editor to open the file.  Type **`vim myday.txt<ENTER>`**.

```bash
$ vim myday.txt
```

You'll now see what you typed and saved into the file.  Because we aren't making any changes and don't want to save any changes, we can exit with **`:q!<ENTER>`**.
