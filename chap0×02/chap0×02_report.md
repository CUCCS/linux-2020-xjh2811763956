# From GUI to CLI


## 软件环境
* asciinema
* Ubuntu 18.04.4 Server 64bit
  
## 实验过程
* [lesson_1](https://asciinema.org/a/7L5RgfzWj4o2LtAcrkotnNRwJ)

* [lesson_2](https://asciinema.org/a/wVYF4DVMjXnDDBVp1clfEu2Z5)

* [lesson_3](https://asciinema.org/a/WJUfMwZptqJyfYF6zBBZjcOga)

* [lesson_4](https://asciinema.org/a/G0bN0UOVdXgRrtgoW0Otpt16r)

* [lesson_5](https://asciinema.org/a/Jolz3s6QGqvUHCuxaVhJS18M0)

* [lesson_6](https://asciinema.org/a/PQLx7F2H0tVEiuMv5tIxnZ1HG)

* [lesson_7](https://asciinema.org/a/bg1V092EphAbmssiYqr4pu4Wl)
  
## 实验问题
### 你了解vim有哪几种工作模式？
  * Nomal mode
  * Insert mode
  * Visual mode

### Normal模式下，从当前行开始，一次向下移动光标10行的操作方法？如何快速移动到文件开始行和结束行？如何快速跳转到文件中的第N行？
* 一次向下移动光标10行 `10j`
* 移动到文件开始行和结束行——`gg`(开始行)、`G`(结束行)
* 快速跳转到文件中的第N行——`Ngg`、`NG`（无需回车）、`:N` (需要回车)
  
### Normal模式下，如何删除单个字符、单个单词、从当前光标位置一直删除到行尾、单行、当前行开始向下数N行？
* 删除单个字符：`x`
* 删除单个单词：`dw`
* 删除到行尾：`d$`
* 删除单行：`dd`
* 删除下N行：`Ndd`

### 如何在vim中快速插入N个空行？如何在vim中快速输入80个-？
* 插入N个空行：`No` （在光标下方插入）、`NO`(在光标上方插入)
* 快速插入80个-：`80i-`

### 如何撤销最近一次编辑操作？如何重做最近一次被撤销的操作？
* 撤销最近一次编辑操作：`u`
* 重做最近一次被撤销的操作：`Ctrl+R`

### vim中如何实现剪切粘贴单个字符？单个单词？单行？如何实现相似的复制粘贴操作呢？
#### 剪切
* 剪切单个字符：`x`
* 剪切单个单词：`dw`
* 剪切单行：`dd`
* 剪切至行尾：`d$`

#### 复制
* 复制单个字符：`y`
* 复制单个单词：`yw`
* 复制单行：`yy`

#### 粘贴
* 粘贴：`p`(粘贴至光标后)、`P`(粘贴至光标前)

 
### 为了编辑一段文本你能想到哪几种操作方式（按键序列）？
* 移动光标：`H`(左)、`J`(下)、`K`(上)、`L`(右)
* 移动到下N个单词的开头和结尾：`Nw`、`Ne`
* 查询：`/关键词`
* 剪切字符：`x`
* 替换字符：`r`
* 批量替换：`%s/old/new/g`
* 撤销上一步：`u`
* 退出：`:q`、`:wq`

### 查看当前正在编辑的文件名的方法？查看当前光标所在行的行号的方法？
* `Ctrl+g`

### 在文件中进行关键词搜索你会哪些方法？如何设置忽略大小写的情况下进行匹配搜索？如何将匹配的搜索结果进行高亮显示？如何对匹配到的关键词进行批量替换？
* 关键词搜索：`/关键词`
* 设置忽略大小写：`:set ic`
* 高亮显示搜索结果：`:set hlsearch`
* 关键词进行批量替换：`:%s/old/new/g`

### 在文件中最近编辑过的位置来回快速跳转的方法？
* `Ctrl+o`、`Ctrl+i`

### 如何把光标定位到各种括号的匹配项？例如：找到(, [, or {对应匹配的),], or }
* 光标在某个单个括号上+`%`

### 在不退出vim的情况下执行一个外部程序的方法？
* `:!外部程序名`

### 如何使用vim的内置帮助系统来查询一个内置默认快捷键的使用方法？如何在两个不同的分屏窗口中移动光标？
* 查询一个内置默认快捷键 :* `help 快捷键`
* 在两个不同的分屏窗口中移动光标：`:set mouse=a`(打开鼠标功能)+`Ctrl+w`(窗口切换)