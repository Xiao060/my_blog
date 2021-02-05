<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Operations of vim](#operations-of-vim)
  - [Move](#move)
    - [left,down,up,right](#leftdownupright)
    - [move in row](#move-in-row)
    - [move between rows](#move-between-rows)
    - [move screen](#move-screen)
    - [move between paragraghs](#move-between-paragraghs)
    - [move between brackets](#move-between-brackets)
  - [Edit](#edit)
    - [Insert](#insert)
    - [Mark](#mark)
    - [Choose](#choose)
    - [Undo and Redo](#undo-and-redo)
    - [Delete](#delete)
    - [Copy and Paste](#copy-and-paste)
    - [Indent and Repeat](#indent-and-repeat)
    - [Find](#find)
    - [Replace](#replace)
  - [Split screen](#split-screen)

<!-- /code_chunk_output -->

# Operations of vim

## Move

### left,down,up,right
|命令 |功能  |
|:---:|:---:|
|h    |向左  |
|j    |向下  |
|k    |向上  |
|l    |向右  |

### move in row
|命令 |英文  |功能 |
|:---:|:---:|:---:|
|w    |word |向后移动一个单词|
|b    |back |向前移动一个单词|
|0    |     |行首|
|^    |     |行首，第一个不是空白字符的位置|
|$    |     |行尾|

### move between rows
|命令      |英文  |功能   |
|:--------:|:---:|:-----:|
|gg        |go   |文件顶部|
|G         |go   |文件末尾|
|**num** gg|go   |移动到 num 对应行数|
|**num** G |go   |移动到 num 对应行数|
|:**num**  |     |移动到 num 对应行数|

### move screen
|命令  |英文    |功能   |
|:----:|:-----:|:-----:|
|Ctrl b|back   |向上翻页|
|Ctrl f|forward|向下翻页|
|H     |head   |屏幕顶部|
|M     |middle |屏幕中间|
|L     |low    |屏幕底部|

### move between paragraghs
|命令 |功能  |
|:---:|:---:|
|{    |上一段|
|}    |下一段|

### move between brackets
|命令 |功能         |
|:---:|:----------:|
|%    |括号匹配及切换|


## Edit

### Insert
|命令 |英文   |功能 |  
|:---:|:----:|:---:|
|i    |insert|在当前字符前插入文本|
|I    |insert|在行首插入文本|
|a    |append|在当前字符后插入文本|
|A    |append|在行末添加文本|
|o    |      |在当前行后面插入一行|
|O    |      |在当前行前面插入一行|


### Mark
|命令        |英文  |功能   |
|:----------:|:---:|:-----:|
|m **letter**|mark |添加标记 letter|
|' **letter**|     |定位到标记 letter 所在位置|

### Choose
|命令  |模式        |功能   |
|:----:|:---------:|:-----:|
|v     |**可视模式**|从光标位置开始按照正常模式选择文本|
|V     |可视行模式  |选中光标经过的完整行|
|Ctrl v|可视块模式  |垂直方向选中文本|

### Undo and Redo
|命令  |英文  |功能         |
|:----:|:---:|:-----------:|
|u     |undo |撤销上次命令  |
|Ctrl r|redo |恢复撤销的命令|

### Delete
|命令 |英文   |功能         |
|:---:|:----:|:-----------:|
|x    |cut   |删除光标所在字符，或者选中文字|
|d    |delete|删除移动命令对应的内容|
|dd   |delete|删除光标所在行，可以 ndd 剪切多行|
|D    |delete|删除至行尾|
|**d** 常与移动命令连用|
|dw   |      |从光标位置删除到单词末尾|
|d0   |      |从光标位置删除到一行的起始位置|
|d}   |      |从光标位置删除到段落结尾|
|ndd  |      |从光标位置向下连续删除 n 行|
|d **num** G||从光标所在行删除到 num行 之间的所有代码|
|d 'letter|   |从光标所在行删除到标记 letter 之间的所有代码|

### Copy and Paste
|命令 |英文  |功能 |
|:---:|:---:|:---:|
|y    |copy |复制|
|yy   |copy |复制一行，可以 nyy 复制多行|
|p    |paste|粘贴|

### Indent and Repeat
|命令 |功能  |
|:---:|:---:|
|>>   |向右增加缩进|
|<<   |向左减少缩进|
|可视模式下，仅需一个 **<** 或 **>**||
|.    |重复上次命令|
    
### Find
|命令     |功能  |
|:-------:|:---:|            
|/**str** |查找 **str**|
|n        |查找下一个|
|N        |查找上一个|
|*        |向后查找当前光标所在单词|
|#        |向前查找当前光标所在单词|

### Replace 
|命令 |英文    |模式       |功能 |
|:---:|:-----:|:---------:|:---:|
|r    |replace|命令模式    |替换当前字符|
|R    |replace|**替换模式**|替换当前行光标后的字符|
|:%s/oldstr/newstr/g ||末行模式|全局替换|
|:s/oldstr/newstr/g  ||可视模式|可视区域替换|
|:%s/oldstr/newstr/gc||末行模式|确认替换|


## Split screen
|命令        |英文           |功能 |
|:----------:|:------------:|:---:|
|:sp [文件名] |split         |横向增加分屏|
|:vsp [英文名]|vertical split|纵向增加分屏|
|w            |window        |切换到下一个窗口|
|r            |reverse       |互换窗口|
|c            |close         |关闭当前窗口，但是不能关闭最后一个窗口|
|q            |quit          |退出当前窗口，如果是最后一个窗口，则关闭 vi|
|o            |other         |关闭其他窗口|
|+            |              |增加窗口高度|
|-            |              |减少窗口高度|
|>            |              |增加窗口宽度|
|<            |              |减少窗口宽度|
|=            |              |等分窗口大小|