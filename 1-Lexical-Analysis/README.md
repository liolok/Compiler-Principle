# 词法分析

## 待分析的简单词法

### 关键词

`begin` `if` `then` `while` `do` `end`

### 运算符和界符

`:` `:=` `+` `-` `*` `/` `<` `<=` `<>` `>` `>=` `=` `;` `(` `)` `#`

### 标识符和整数常量

ID = letter(letter|digit)*

INT = digit+

### 空白

空格、制表符、换行符。

## 各种单词符号对应的种别码

| 单词符号 | 种别码 |
|----------|--------|
| `begin`  | 1      |
| `if`     | 2      |
| `then`   | 3      |
| `while`  | 4      |
| `do`     | 5      |
| `end`    | 6      |
| ID       | 10     |
| INT      | 11     |
| `+`      | 13     |
| `-`      | 14     |
| `*`      | 15     |
| `/`      | 16     |
| `:`      | 17     |
| `:=`     | 18     |
| `<`      | 20     |
| `<>`     | 21     |
| `<=`     | 22     |
| `>`      | 23     |
| `>=`     | 24     |
| `=`      | 25     |
| `;`      | 26     |
| `(`      | 27     |
| `)`      | 28     |
| `#`      | 0      |

## 词法分析程序功能

### 输入

所给文法的程序源码字符串

### 输出

二元组 `(code, value)` 构成的序列，其中：
- `code` 为整型种别码；
- `value` 为单词的值，类型为字符串或整数。

以源码 `begin x:=9; if x>9 then x:=2*x+1/3; end #` 为例，输出如下：

`(1,begin)` `(10,x)` `(18,:=)` `(11,9)` `(26,;)` `(2,if)` ...
