---
title: R base 中的字符串处理函数
author: yuanfan
date: 2024-09-13T22:50:17+0800
slug: r base string
categories:
  - R
tags:
  - R
draft: no
---



<!--more-->

本文将依照功能来介绍 R base 中的字符串处理函数。

# 一、计算长度 nchar

通常用`nchar()`函数来计算字符串的字符数或者字节数，用`length()`函数来计算向量的长度（PS.在 sql 语言中用`length()`函数来计算字符数）。

下面先从字符、字节的定义以及编码标准开始，先稍微了解一下基础定义可以少踩点坑。

## 1.1. 字符、字节、编码标准

字符（Character）是计算机中文本的最小单位，有许多类型如数字、字母、符号等，一串字符组合起来就是字符串（String），在 R 中通常由单引号或双引号包裹起来。

字节（Byte）是计算机中数据处理的最小单位，通常由8位二进制数字（8bits）组成，一位二进制数字（0或1）是计算机中数据存储的最小单位。

而字符与字节的关系在不同的编码标准下，有所不同。

1. ASCII 编码，是最早诞生的字符编码标准，[ASCII 字符集](https://www.asciim.cn/)共有128个字符，包括大写字母、小写字母、（阿拉伯）数字等，均用一个字节代表一个字符。

2. ANSI 编码，是一种关于编码方式和存储方式的方案标准，通常用1到2个字节代表1个字符，ANSI 字符集中前128个与 ASCII 码保持一致，后面的由不同的国家或地区基于各自的需求来制定，因而也衍生出许多不同的字符编码方案。这些编码方案在 Windows 系统中被称为代码页（Code Page）：比如支持简体中文的代码页编号是936，对应的 ANSI 标准是 GB2312；支持英语及其他西欧语言的代码页编号是1252，对应的 ANSI 标准是 ISO 8859-1（Latin-1）；支持繁体中文的代码页编号是950，对应的 ANSI 标准是 Big5。

3. GB2312编码，是中国发布的汉字编码标准，后来扩展成 GBK，又扩展成 GB18030。

4. Unicode 编码，是几乎能够覆盖世界上所有字符的统一编码标准，在[Unicode 符号表](https://symbl.cc/cn/unicode-table/)中，不同语言的不同符号都有唯一对照的编码。最常用的存储方式有UTF-8（每个字符由1到4个字节组成）、UTF-16（每个字符由2到4个字节组成）、UTF-32（每个字符固定由4个字节组成）。

在 R 中，执行`Encoding()`函数可以将字符向量识别为四种不同的编码标准和存储格式：UTF-8（Unicode 编码）、Latin-1（ISO 8859-1）、Bytes（非 ASCII 字符的原始字节）、unknown（本地或未指定的编码）。

## 1.2. 字符数、字节数

R 中常见字符除了数字、英文字母、中文以外，还有一些具有特殊含义的字符，如 NA（Not Avaliable，缺失值）、Inf（Infinite，无穷大）、NaN（Not a Number，非数值）、NULL（空值），下面分别对其使用`nchar()`函数来计算字符数和字节数，我们可以得出以下结论。

+ 汉字，被存储为 UTF-8 格式，一个汉字字符的字节数为3。
+ 英文字母、数字以及 Inf/-Inf/NaN 等特殊字符，都是单字节字符，字符数与字节数一致。
+ NA 在默认情况下不被处理，如果设置`keepNA = FALSE`参数，那么 NA 才会被当做字符处理，其字符数就是2。
+ NULL 会被忽略。
+ `\u2764`是编程语言中的 Unicode 转义序列，代表的字符就是❤，因此两者都是1个字符、3个字节。


```r
my_vector <- c("汉字",
               "Ear1",
               NA,
               Inf,
               -Inf,
               NaN,
               "",
               " ",
               NULL,
               '\u2764',
               "❤",
               '∠( ᐛ 」∠)_')

# 计算向量长度
length(my_vector)
## [1] 11

# 查看字符串的编码格式
Encoding(my_vector)
##  [1] "UTF-8"   "unknown" "unknown" "unknown" "unknown" "unknown" "unknown"
##  [8] "unknown" "UTF-8"   "UTF-8"   "UTF-8"

nchar(my_vector)
##  [1]  2  4 NA  3  4  3  0  1  1  1  9
nchar(my_vector, keepNA = FALSE)
##  [1] 2 4 2 3 4 3 0 1 1 1 9
nchar(my_vector, type = 'bytes')
##  [1]  6  4 NA  3  4  3  0  1  3  3 17
```

`nchar()`函数默认所需输入的是字符向量，如果输入的是其他数据类型，会自动用`as.character()`函数进行强制转换，而不会报错。如下可知，缺失值 NA 若作为列表来计算字符数，会先强制转换成字符串`"NA"`，从而得到字符数为2。


```r
nchar(list(NA))
## [1] 2
as.character(list(NA))
## [1] "NA"
nchar(as.character(list(NA)))
## [1] 2
```

## 1.3. 用长度比较差异

下面有两个极为相似的字符串，字符数一致但并不相等。如果进一步比较两个字符串的字节数，发现也不一致。


```r
str1 <- "财政部 卫生健康委"
str2 <- "财政部 卫生健康委"

# 计算字符数
nchar(str1)
## [1] 9
nchar(str2)
## [1] 9

str1 == str2
## [1] FALSE

# 计算字节数
nchar(str1, type = 'bytes')
## [1] 27
nchar(str2, type = 'bytes')
## [1] 25
```

如果将这两个字符串分别转换成 raw 格式，即存储的原始16进制字节序列，再进一步比较转换后存在的差异，可以看到前者独有“e2 80 82”（代表半个空格，EN SPACE），后者独有“20”（代表一个普通空格，SPACE）。


```r
raw1 <- charToRaw(str1)
raw2 <- charToRaw(str2)
print(raw1)
##  [1] e8 b4 a2 e6 94 bf e9 83 a8 e2 80 82 e5 8d ab e7 94 9f e5 81 a5 e5 ba b7 e5
## [26] a7 94
print(raw2)
##  [1] e8 b4 a2 e6 94 bf e9 83 a8 20 e5 8d ab e7 94 9f e5 81 a5 e5 ba b7 e5 a7 94

# 比较差异，raw1 有，raw2无
setdiff(as.character(raw1), as.character(raw2))
## [1] "e2" "80" "82"

# 比较差异，raw1 无，raw2有
setdiff(as.character(raw2), as.character(raw1))
## [1] "20"
```

如果再把这两个16进制字节序列转换为字符串，用普通的眼睛看也还是很难看出区别。


```r
rawToChar(as.raw(c(0xe2, 0x80, 0x82)))
## [1] " "
rawToChar(as.raw(c(0x20)))
## [1] " "
```

# 二、拼接 paste

通常使用`paste()`函数来拼接字符串，下面是把多个字符串拼接成一个长字符串的情况，默认的分隔符是一个空格，可以通过 sep（seperate）参数来设置其他分隔符。也可设置`sep=""`，使拼接的字符串之间不存在分隔符。其中，`paste(..., sep = "")`可用`paste0(...)`代替。

另外 `cat()`函数也可以用来拼接字符串，只是结果会直接输出到控制台（Console），并且不能被赋值给 R 中的变量。


```r
paste('春江', '花月夜', "❤")
## [1] "春江 花月夜 ❤"
paste('春江', '花月夜', "❤", sep = "|")
## [1] "春江|花月夜|❤"
paste('春江', '花月夜', "❤", sep = "")
## [1] "春江花月夜❤"
paste0('春江', '花月夜', "❤")
## [1] "春江花月夜❤"

cat('春江', '花月夜', "❤")
## 春江 花月夜 ❤
```

下面的例子是按行分组拼接字符串，使用`paste()`函数把向量中多个元素拼接成一个长字符串，这里就需要通过 collapse 参数来设置分隔符。由于 collapse 参数的默认值是 NULL，所以如果不设置这个参数，就不会把向量中的元素拼接起来。


```r
data <- data.frame(
  id = c(1:2),
  col1 = c('春江', '海上'),
  col2 = c('潮水', '明月'),
  col3 = c('连海平', '共潮生')
)

apply(X = data[, 2:4], MARGIN = 1, FUN = paste)
##      [,1]     [,2]    
## [1,] "春江"   "海上"  
## [2,] "潮水"   "明月"  
## [3,] "连海平" "共潮生"
apply(X = data[, 2:4], MARGIN = 1, FUN = paste, collapse = "")
## [1] "春江潮水连海平" "海上明月共潮生"
```

# 三、分割 strsplit

通常使用`strsplit()`函数来分割字符串，其中用 split 参数来设置需要匹配的分割符号。如下所示，若要精确匹配“|”符号后分割字符串，在参数设置上需要增加`fixed = TRUE`，或者改写作`split = '[|]'`、`split = '\\|'`。


```r
strsplit('潮水|流水', split = ',')
## [[1]]
## [1] "潮水|流水"
strsplit('潮水|流水', split = '|')
## [[1]]
## [1] "潮" "水" "|"  "流" "水"

strsplit('潮水|流水', split = '|', fixed = TRUE)
## [[1]]
## [1] "潮水" "流水"
strsplit('潮水|流水', split = '[|]')
## [[1]]
## [1] "潮水" "流水"
strsplit('潮水|流水', split = '\\|')
## [[1]]
## [1] "潮水" "流水"
```

split 参数支持使用正则表达时，比如输入多个不同的分割符号，但在复杂的情况下容易产生空字符串。


```r
strsplit('春江 潮水*连海平*|海上', split = '[ |*]')
## [[1]]
## [1] "春江"   "潮水"   "连海平" ""       "海上"
```

如果所需设置的分割符号在字符串的开头或者末尾，那么精确匹配并分割后，在开头的情况会多一个空字符串，而结尾不会。


```r
strsplit(c('忽闻海上有仙山', '山在虚无缥缈间'), split = '[山]')
## [[1]]
## [1] "忽闻海上有仙"
## 
## [[2]]
## [1] ""             "在虚无缥缈间"

unlist(strsplit(c('忽闻海上有仙山', '山在虚无缥缈间'), split = '[山]'))
## [1] "忽闻海上有仙" ""             "在虚无缥缈间"
```

使用`strsplit()`函数得到的结果会是一个列表，通常可以再加上`unlist()`函数转换成向量。


```r
data <- data.frame(id = c(1:2), value = c('江水|为竭', '海枯|石烂'))

unlist(lapply(data[, 2], function(x)
  strsplit(x, split = '[|]')))
## [1] "江水" "为竭" "海枯" "石烂"
```

# 四、截取子集

## 4.1. 指定起终点位置取子集 substr/substring

`substr()`和`substring()`都能实现截取字符串的功能，在截取单个字符串的情况下，如果起点位置和终点位置分别只输入一个数字，那么两个函数会输出一样的结果，且后者可以只需输入起点位置、默认截取到最长的终点。


```r
substr('阿木是条狗', start = 4, stop = 5)
## [1] "条狗"
substring('阿木是条狗', first = 4, last = 5)
## [1] "条狗"
substring('阿木是条狗', first = 4)
## [1] "条狗"
```

在单个字符串的情况下，`substr()`不管起点和终点输入多少个数字，只分别按第一个数字输出结果，而`substring()`允许输入多个不同的起点终点位置。


```r
substr('阿木是条狗', 1:4, 2:5)
## [1] "阿木"

substr(rep('阿木是条狗', 4), 1:4, 2:5)
## [1] "阿木" "木是" "是条" "条狗"
substring('阿木是条狗', 1:4, 2:5)
## [1] "阿木" "木是" "是条" "条狗"

substring('阿木是条狗', 1, 2:5)
## [1] "阿木"       "阿木是"     "阿木是条"   "阿木是条狗"
```

## 4.2. 截取固定宽度的子集 strtrim

`strtrim()`函数按照固定宽度从第一个字符开始截取字符串。在截取英文字符串的情况下，指定宽度为数字几，就会截取多少个字符。在截取中文字符串的情况下，一个中文字符占2个宽度，不足2个宽度时输出结果为空字符串。


```r
strtrim('amu is a dog', width = 3)
## [1] "amu"
strtrim(rep('阿木是条狗', 10), c(1:10))
##  [1] ""           "阿"         "阿"         "阿木"       "阿木"      
##  [6] "阿木是"     "阿木是"     "阿木是条"   "阿木是条"   "阿木是条狗"
```

## 4.3. 去掉左右两边的字符 trimws

`trimws()`函数可以去掉字符串中各类字符，但仅限于去掉字符串最左边或最右边或两边的字符，至于具体要去掉哪些字符由 whitespace 参数来指定。

+ `\t`，代表匹配制表符（tab）。
+ `\n`，代表匹配换行符（new line）。
+ `\r`，代表匹配回车符（return）。
+ `\\h`，代表匹配`\h`，即所有水平（horizontal）空白符。
+ `\\v`，代表匹配`\v`，及所有垂直（vertical）空白符。

除了以上符号，还可以用`\\`加上其他符号来匹配并去除。


```r
my_vector <- c('
  
    amu is a dog   ','中文 amu is a dog * ')
my_vector
## [1] "\n  \n    amu is a dog   " "中文 amu is a dog * "
trimws(my_vector, whitespace = "[ \t\r\n]")
## [1] "amu is a dog  "      "中文 amu is a dog *"
trimws(my_vector, whitespace = "[\\h\\v]")
## [1] "amu is a dog"        "中文 amu is a dog *"
trimws(my_vector, whitespace = "[\\h\\v\\*\\中文]")
## [1] "amu is a dog" "amu is a dog"
```

# 五、替换

## 5.1. 转换大小写 tolower/toupper

+ `tolower()`：大写转（to）小写（lower）。
+ `toupper()`：小写转（to）大写（upper）。
+ `casefold()`：默认大写转小写，若设置`upper = TRUE`则为小写转大写。


```r
tolower('AMU is A dog')
## [1] "amu is a dog"
toupper('amu is a dog')
## [1] "AMU IS A DOG"
casefold('AMU is A dog') # 默认大小转小写
## [1] "amu is a dog"
casefold('AMU is A dog', upper = TRUE)
## [1] "AMU IS A DOG"
```

## 5.2. 替换字符串 chartr/sub/gsub

`chartr/sub/gsub`这三个函数都能实现替换字符的功能，但`chartr()`函数的替换功能较为单一，先看`chartr()`函数的特点，有以下几点。

1. 函数应用范围：可以是单个字符串，或者字符向量。
2. 替换的范围：所有能匹配上的字符。
3. 匹配的参数：仅能指定固定的一个或多个字符，不支持正则表达式；指定多个字符时，也相当于一对一的替换。


```r
chartr(old = "狗", new = "猫", x = '阿木是条狗')
## [1] "阿木是条猫"
chartr(old = "狗", new = "猫咪", x = '阿木是条狗')
## [1] "阿木是条猫"

# 相当于指定 条->猫，狗->咪
chartr(old = "条狗", new = "猫咪", x = '阿木是条狗，小白也是狗')
## [1] "阿木是猫咪，小白也是咪"

chartr('g', 'G', x = c('pig', 'dog'))
## [1] "piG" "doG"
chartr('*', ' ', x = c('pig*', 'dog*'))
## [1] "pig " "dog "
```

相较于`chartr()`函数，`sub()`和`gsub()`函数还支持正则表达式（sub 代表 substitute，替换），但`sub()`仅会替换所匹配到的第一处字符串。

|功能|chartr|sub|gsub|
|:-------------:|:--:|:--:|:--:|
|替换所有匹配的字符|✓|×|✓|
|支持正则表达式|×|✓|✓|
|支持不区分大小写|×|✓|✓|


```r
my_vector <- c('>amu<;>money<', 'MuMu')
chartr('M', '木', my_vector)
## [1] ">amu<;>money<" "木u木u"
sub('M', '木', my_vector, ignore.case = TRUE)
## [1] ">a木u<;>money<" "木uMu"
gsub('M', '木', my_vector, ignore.case = TRUE)
## [1] ">a木u<;>木oney<" "木u木u"

gsub(pattern = '[><]', replacement = "", my_vector)
## [1] "amu;money" "MuMu"
```

## 5.3. 替换元素 replace

`replace()`函数可用来替换字符向量中的元素，但需要指定所替换的元素在向量中的索引（PS.在 sql 语言中用`replace()`函数来计算字符串）。


```r
my_vector <- c('张三', '李四', '王七', '赵六', '阿木')
replace(my_vector, '王七', '王五')
##                                      王七 
## "张三" "李四" "王七" "赵六" "阿木" "王五"
replace(my_vector,
        list = c(3, 5),
        values = c('王五', '其他'))
## [1] "张三" "李四" "王五" "赵六" "其他"
```

# 六、模式匹配

## 6.1. 匹配字符串

R base 中支持使用正则表达式来匹配字符串的函数有`grep/agrep/grepl/regexpr/gregexpr/regexec/gregexec`，这些函数名称相似、功能相近，特别容易弄混。

首先，看看这些函数名称的组成部分，如下可知，以英文字母 g 开头的函数带有“全局”的含义。

|函数名称中的字符|英文释义|中文释义|
|:----:|:----:|:----:|
|rep|regular expression|正则表达式|
|g|global|全局|
|a|approximate|近似，模糊|
|l|logical|逻辑|
|reg|regular|正则的|
|expr|expression|表达式|
|exec|execute|执行|

其次，这些支持正则表达式的函数都有下面这几个参数。

+ ignore.case：是否忽略大小写，默认值为 FALSE，代表区分大小写，取值为 TRUE 时代表不区分大小写。
+ perl：是否兼容 perl 语言下的正则表达式，默认值为 FALSE，代表不兼容。
+ fixed：是否仅匹配字符串，默认值为 FALSE。
+ useBytes：是否按字节匹配，默认值为 FALSE。

再次，将这些函数分成四组来进行了解。

第一组，`grep/agrep/grepl`，返回匹配成功的字符串在向量中的位置。

第二组，`regexpr/gregexpr`与`regexec/gregexec`，相比第一组更精细，返回匹配成功的部分在字符串中的位置。

第三组，`regmatches`，根据第二组的结果从字符串中抽取匹配成功的部分。

### 6.1.1. grep/agrep/grepl

`grep/agrep/grepl`这组函数的名称中都有 g 和 rep，分别对应 global 和 regular expression，即支持正则表达式且全局匹配。具体功能上的差异如下表所示。

|功能|grep|agrep|grepl|
|:----------:|:----:|:----:|:----:|
|支持正则表达式、全局匹配|✓|✓|✓|
|支持模糊匹配|×|✓|×|
|返回匹配成功的元素的位置|✓|✓|×|
|返回匹配成功的元素|✓|✓|×|
|返回匹配成功或失败的 TRUE/FALSE 值|×|×|✓|

在下面的例子中，`pattern = '[>.<]'`表示匹配方括号中`>`、`.`、`<`三个之中任意一个字符，`pattern = '>.*<'`表示匹配在`>`与`<`之间存在任意数量的字符。


```r
my_vector <- c('>阿木<;>曼妮<', 'amu', 'amu<', '>.*<')
# 默认情况下，返回匹配成功的元素索引
grep(pattern = '[>.<]', my_vector)
## [1] 1 3 4
grep(pattern = '>.*<', my_vector)
## [1] 1 4

# 设置 value = TRUE ，返回匹配成功的字符串
grep(pattern = '[>.<]', my_vector, value = TRUE)
## [1] ">阿木<;>曼妮<" "amu<"          ">.*<"

# 设置 invert = TRUE，返回匹配不成功的元素索引
grep(pattern = '[>.<]', my_vector, invert = TRUE)
## [1] 2

# 设置 fixed = TRUE，返回把'>.*<'当做字符串匹配成功的元素索引
grep(pattern = '>.*<', my_vector, fixed = TRUE)
## [1] 4

# 返回每个元素是否匹配成功的 TRUE/FALSE 结果
grepl(pattern = '[>.<]', my_vector)
## [1]  TRUE FALSE  TRUE  TRUE

# 返回模糊匹配成功的元素索引
agrep(pattern = '阿木狗', my_vector)
## [1] 1
agrep(pattern = '阿木狗', my_vector, value = TRUE)
## [1] ">阿木<;>曼妮<"
```

### 6.1.2. regexpr/gregexpr/regexec/gregexec

`regexpr/gregexpr`与`regexec/gregexec`这两组函数的名称中都 rep，对应 regular expression，即支持正则表达式。从函数名称来看，两组函数在具体功能上的差异如下表所示。

|功能|regexpr|gregexpr|regexec|gregexec|
|:----------:|:----:|:----:|:----:|:----:|
|reg，返回在字符串中第一次成功匹配的字符起始位置|✓|×|✓|×|
|greg，返回在字符串中全部成功匹配的字符起始位置|×|✓|×|✓|
|expr，支持一个捕获组`()`|✓|✓|×|×|
|exec，支持多个捕获组`()`|×|×|✓|✓|

为了详细了解这两组函数更多的差异细节，接下来进行分组对比。

+ 对比 `grep()`与`regexpr()`，下例中`pattern = '狗|猫咪'`表示匹配含有“狗”或“猫咪”的字符串。
  - `grep()`函数返回一个向量，即模式匹配成功的字符串在向量中的位置，匹配失败的不输出。
  - `regexpr()`函数返回一个向量，匹配成功的模式在字符串中的起始位置、模式的长度，匹配失败的输出-1。


```r
my_vector <- c('阿木狗', '猫咪曼妮', '图图')

grep(pattern = '狗|猫咪', my_vector)
## [1] 1 2

regexpr(pattern = '狗|猫咪', my_vector)
## [1]  3  1 -1
## attr(,"match.length")
## [1]  1  2 -1
```

+ 对比`regexpr()`和`gregexec()`。
  - `regexpr()`函数返回一个向量，且仅返回第一次匹配成功的模式所对应的结果。
  - `gregexec()`函数返回一个列表，返回每一次匹配成功的模式所对应的结果。


```r
my_vector <- c('条狗阿木狗', '猫咪曼妮猫咪', '图图')

regexpr(pattern = '狗|猫咪', my_vector)
## [1]  2  1 -1
## attr(,"match.length")
## [1]  1  2 -1

gregexpr(pattern = '狗|猫咪', my_vector)
## [[1]]
## [1] 2 5
## attr(,"match.length")
## [1] 1 1
## 
## [[2]]
## [1] 1 5
## attr(,"match.length")
## [1] 2 2
## 
## [[3]]
## [1] -1
## attr(,"match.length")
## [1] -1
```

+ 对比`gregexpr()`和`gregexec()`，分别使用两组不同的模式，并且用`regmatches()`函数提取模式匹配成功的部分。
  - `pattern = '>..<'`表示匹配一个`>`符号跟着两个任意字符再跟着一个`<`符号，比较 reg1 和 reg2 的提取结果，内容基本一致，返回的都是列表，但前者（expr）列表中的元素是向量，后者（exec）列表中的元素是矩阵。
  - `pattern = '(>.)(.<)'`表示匹配两个捕获组，第一个捕获组是`(>.)`代表一个`>`符号跟着一个任意字符，第二个捕获组是`(.<)`代表一个任意字符跟着一个`<`符号，两个捕获组串接也可以匹配`>..<`。比较 reg3 和 reg4 的结果可知，只有后者（exec）才会输出每个捕获组匹配成功的内容。


```r
my_vector <- c('>阿木<;>曼妮<', '>mu<money')
reg1 <- gregexpr(pattern = '>..<', my_vector)
reg2 <- gregexec(pattern = '>..<', my_vector)
reg3 <- gregexpr(pattern = '(>.)(.<)', my_vector)
reg4 <- gregexec(pattern = '(>.)(.<)', my_vector)

regmatches(my_vector, reg1)
## [[1]]
## [1] ">阿木<" ">曼妮<"
## 
## [[2]]
## [1] ">mu<"
regmatches(my_vector, reg2)
## [[1]]
##      [,1]     [,2]    
## [1,] ">阿木<" ">曼妮<"
## 
## [[2]]
##      [,1]  
## [1,] ">mu<"
regmatches(my_vector, reg3)
## [[1]]
## [1] ">阿木<" ">曼妮<"
## 
## [[2]]
## [1] ">mu<"
regmatches(my_vector, reg4)
## [[1]]
##      [,1]     [,2]    
## [1,] ">阿木<" ">曼妮<"
## [2,] ">阿"    ">曼"   
## [3,] "木<"    "妮<"   
## 
## [[2]]
##      [,1]  
## [1,] ">mu<"
## [2,] ">m"  
## [3,] "u<"
```

### 6.1.3. regmatches

`regmatches()` 用于根据 `regexpr()`、`gregexpr()` 、 `regexec()`、`gregexec()` 的结果提取匹配的子字符串。

如下，希望提取`>`与`<`符号之间的名称，名称长度不限，用`gregexpr + regmatches + gsub`来实现。


```r
my_vector <- c('>木<;>土豆<', '>>图图狗<')

# 步骤1：使用 gregexpr 得到匹配成功的子字符串的起始位置和长度
step1 <- gregexpr(pattern = ">([^<]+)<", my_vector)
print(step1)
## [[1]]
## [1] 1 5
## attr(,"match.length")
## [1] 3 4
## 
## [[2]]
## [1] 1
## attr(,"match.length")
## [1] 6

# 步骤2：使用 regmatches 继续提取子字符串
step2 <- regmatches(my_vector, step1)
print(step2)
## [[1]]
## [1] ">木<"   ">土豆<"
## 
## [[2]]
## [1] ">>图图狗<"

# 步骤3：使用 gsub 将>和<符号去掉
step3 <- gsub(pattern = '[><]', replacement = "", unlist(step2))
print(step3)
## [1] "木"     "土豆"   "图图狗"
```

在`regmatches()`函数中还可以设置`invert = TRUE`来提取匹配成功后剩下的部分，也可以直接用`regmatches(...) <- value`的方式替换掉匹配成功或者未匹配的部分。


```r
my_vector <- c('>木<;abc>土豆<ef', 'abc>图图狗<wre')

regmatches(my_vector, gregexpr(pattern = ">([^<]+)<", my_vector), invert = TRUE)
## [[1]]
## [1] ""     ";abc" "ef"  
## 
## [[2]]
## [1] "abc" "wre"

regmatches(my_vector, gregexpr(pattern = ">([^<]+)<", my_vector), invert = TRUE) <-
  "**"
print(my_vector)
## [1] "**>木<**>土豆<**" "**>图图狗<**"
```

## 6.2. 匹配元素 match/pmatch/charmatch

+ `match()`：返回 x 中每个元素在 table 中的位置。

+ `pmatch()`：部分匹配（Partial String Matching），返回 x 中每个元素在 table 中能够部分匹配成功的元素的位置。

  - 如果 x 中的元素能与 table 中多个元素部分匹配成功，那么返回第一个位置。
  - 如果 table 中的元素既有和 x 中的元素部分匹配成功，也有完全相等的，那么优先返回完全相等的元素的位置。
  - 如果设置`duplicates.ok = TRUE`，那么 table 中的元素可以重复利用。
  
+ `charmatch()`：几乎相当于`pmatch(..., duplicates.ok = TRUE)`，但是`charmatch()`匹配失败会返回0

|功能|match|pmatch|charmatch|
|:----------------:|:----:|:----:|:----:|
|应用于数值和字符匹配|✓|✓|✓|
|完全匹配|✓|✓|✓|
|部分匹配|×|✓|✓|
|匹配失败的返回值|NA|NA|0|


```r
match(x = 1:10, table = 7:20)
##  [1] NA NA NA NA NA NA  1  2  3  4
match(x = c('a', 'b', 'b'), table = c('b', 'bc'))
## [1] NA  1  1

pmatch(x = c(123, 101), c(1234, 1010))
## [1] 1 2

pmatch(x = c('ab', 'ab', '阿木'),
       table = c('abc', 'cab', '阿木狗'))
## [1]  1 NA  3

pmatch(x = c('ab', 'ab', '阿木'),
       table = c('abc', 'cab', '阿木狗', '阿木狗主'))
## [1]  1 NA NA

pmatch(
  x = c('ab', 'ab', '阿木'),
  table = c('abc', 'ab', '阿木狗主', '阿木狗'),
  duplicates.ok = TRUE
)
## [1]  2  2 NA

charmatch(x = c(123, 101), c(1234, 1010))
## [1] 1 2

charmatch(x = c('ab', 'ab', '阿木'),
       table = c('abc', 'cab', '阿木狗'))
## [1] 1 1 3

charmatch(x = c('ab', 'ab', '阿木'),
       table = c('abc', 'cab', '阿木狗', '阿木狗主'))
## [1] 1 1 0
```

## 6.3. 匹配开头结尾 startsWith/endsWith

`startsWith()`和`endsWith()`用于判断字符串的开头或结尾是否为特定字符。


```r
# 判断第二个参数值‘电’字，是否在第一个参数输入的向量中
startsWith(c('电话', '电脑', '电视机', '电饭煲', '洗衣机'), '电')
## [1]  TRUE  TRUE  TRUE  TRUE FALSE
endsWith(c('电话', '电脑', '电视机', '电饭煲', '洗衣机'), '机')
## [1] FALSE FALSE  TRUE FALSE  TRUE
```

# 七、格式转换（略） 

+ `format()`：主要用于调整日期和数值的格式，功能繁多，暂略。

+ `sprintf()`：按指定格式生成字符串，功能繁多，暂略。

+ `strtoi()`，将其他进制下的数字或字符转换为十进制的整数（int）。比如16进制中下的39，可以转换为10进制下的57。

+ `strwrap()`，将长文本格式化处理为段落，但对中文不起作用。


```r
strtoi(c('阿木', '0x20', 'a', 39), 16L)
## [1] NA 32 10 57

strwrap('我有一头小毛驴，我从来都不骑，有一天我心血来潮骑着去赶集', width = 20)
## [1] "我有一头小毛驴，我从来都不骑，有一天我心血来潮骑着去赶集"
strwrap(
  'I have a donkey that I never ride. One day I suddenly felt like riding it to the market.',
  width = 20
)
## [1] "I have a donkey"     "that I never ride."  "One day I suddenly" 
## [4] "felt like riding it" "to the market."
```

# 八、重复

`rep()`和`strrep()`函数都能生成重复字符串，但前者重复的是元素，后者重复的是字符。


```r
rep(x = 1:2, times = 3)
## [1] 1 2 1 2 1 2
strrep(x = 1:2, times = 3)
## [1] "111" "222"

rep(c('A', 'B', 'C'), 3)
## [1] "A" "B" "C" "A" "B" "C" "A" "B" "C"
strrep(c('A', 'B', 'C'), 3)
## [1] "AAA" "BBB" "CCC"

strrep('A', 1:3)
## [1] "A"   "AA"  "AAA"
strrep(c('A', 'B', 'C'), 1:3)
## [1] "A"   "BB"  "CCC"
```

# 九、交集、并集、差集

取交集、并集、差集的函数既可以应用于字符型向量，也可应用于数值型向量。

+ `intersect()`：取两个向量中元素的交集。
+ `union()`：取两个向量中元素的并集。
+ `setdiff()`：取两个向量中元素的差集，通常是第一个向量中有、第二个向量中无的差集。


```r
my_vector1 <- c(NA, pi, '阿木', '兔狲', NaN)
my_vector2 <- c(pi, NA, '试炼', '意义')

# 交集
intersect(my_vector1, my_vector2)
## [1] NA                 "3.14159265358979"

# 并集
union(my_vector1, my_vector2)
## [1] NA                 "3.14159265358979" "阿木"             "兔狲"            
## [5] "NaN"              "试炼"             "意义"

# 差集，左边有，右边无
setdiff(my_vector1, my_vector2) 
## [1] "阿木" "兔狲" "NaN"

# 判断左边向量的元素是否在右边向量中存在
is.element(my_vector1, my_vector2) 
## [1]  TRUE  TRUE FALSE FALSE FALSE
```

# 十、总结

1. 文中的函数处理的对象是单个字符串或者字符向量，如果直接往函数中输入其他类型的数据，会默认用`as.character()`进行强制转换。如果需要对数据框或列表中的字符串进行处理，通常要结合 apply 族函数。

2. 文中的函数对缺失值的处理各不相同。

  - `strsplit`输出结果中会保留 NA。
  - `sub/gsub`输出结果中会保留 NA，不对 NA 做替换。
  - `grep/grepl`输出结果中会忽略 NA，不匹配 NA。
  - `regexpr/gregexpr/regexec/gregexec`输出结果中也会保留 NA，但结合`regmatches`时不会提取出 NA。


```r
strsplit(c('abc', NA), 'b')
## [[1]]
## [1] "a" "c"
## 
## [[2]]
## [1] NA

sub('.?', "", c('abc', NA))
## [1] "bc" NA

grep('.?', c('abc', NA), value = TRUE)
## [1] "abc"

regexpr('b.', c('abc', NA))
## [1]  2 NA
## attr(,"match.length")
## [1]  2 NA
## attr(,"index.type")
## [1] "chars"
## attr(,"useBytes")
## [1] TRUE
regmatches(c('abc', NA), regexpr('b.', c('abc', NA)))
## [1] "bc"
```

3. 许多时候文本数据都很复杂，需要结合多种字符串函数一起使用。

下面是一个简单的例子，需要从字符串中拆出年份。


```r
data <- data.frame(
  pcode = c('国发〔2024〕10号', '国办发〔2023〕27号'),
  index = c('000014349/2024-00037', '000014349/2023-00047')
)

# 方法一：sub + strsplit 先将分割符替换成一样的，然后分列
sapply(strsplit(sub("/", "-", data$index), "-", fixed = TRUE), "[", 2)
## [1] "2024" "2023"
sapply(strsplit(sub("〔", "〕", data$pcode), "〕", fixed = TRUE), "[", 2)
## [1] "2024" "2023"

# 方法二：regexpr + regmatches + gsub 先用正则表达式提取子字符串，然后去掉多余符号
gsub('[〔〕]', '', regmatches(data$pcode, regexpr('〔.{4}〕', data$pcode)))
## [1] "2024" "2023"
gsub('[/-]', '', regmatches(data$index, regexpr('/.{4}-', data$index)))
## [1] "2024" "2023"
```

# 附：正则表达式

[正则表达式（Regular Expressions）](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F)历史悠久，是一种用来对字符串进行模式匹配的工具，执行`??regex`可以查看 R 中正则表达式用法的一些特色，关于正则表达式的使用细节见本文附录。

暂且先不论如何学习正则表达式，试想一下如果我们要从一段长长的字符串中匹配到想要的内容，那么应该用什么来代表想要的内容，这又需要一些什么功能？

1. 首先，要确定想要的内容是什么结构，或者是什么规则，比如想要以什么开头、以什么结尾、匹配任意字符还是固定字符、匹配一组还是多组不同的内容等等，这类与结构或规则相关的功能若能用简单的字符表达，可以取名为“元字符”。

2. 其次，如果情况更复杂一点，我们希望还能设定匹配成功的内容在长长字符串中出现的次数，可以限定次数为固定数值，或者限定次数为固定范围，这类与控制匹配次数相关的功能若也用简单的字符表达，就叫“限定符”。

3. 再次，字符的种类实在太多，如果能够预先定义好一些常用的字符类别，那么使用起来效率会更高，比如可以预先定义好任意数字、任意字母、任意空白符，这类预先定义的字符类别也要取个名字，就叫“预定义字符”。

4. 最后，由于已经定义了许多不同的符号代表不同的功能，那么这些功能性符号的优先级就必须是一个固定的顺序，这样才能确保不同功能在使用的时候不会冲突。

## 1. 转义符

正则表达式中有些字符具有特殊含义（如`.*+?()[]{}|^$\`），要想特殊字符被当做普通字符来匹配，那么需要在这些符号前面加上转义符。在 R 中，正则表达式的反斜杠符号需要进行双重转义，即写作`\\`。 


```r
# '\\*\\|'代表匹配‘*|’
grep(pattern = '\\*\\|',
     x = c('a*|b', '阿木*', '曼|妮'),
     value = TRUE)
## [1] "a*|b"

# '\\*|\\|'代表匹配*或|
grep(pattern = '\\*|\\|',
     x = c('a*|b', '阿木*', '曼|妮'),
     value = TRUE)
## [1] "a*|b"  "阿木*" "曼|妮"
```

## 2. 元字符

元字符，用于定义匹配模式的基本结构和规则。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`.`|匹配任意单个字符|-|
|`^`|匹配输入字符串的开始位置|-|
|`$`|匹配输入字符串的结束位置|-|
|`[]`|匹配括号内的任意一个字符|比如`[0-9]`匹配0到9之间任意一个数字|
|`()`|用于分组匹配和捕获子表达式|比如`(xyz)`匹配并捕获"xyz"|


```r
# 默认情况下'.'能匹配出换行符（`\n`）和回车符（`\r`）
grep(pattern = '.',
     x = c('\n', '\r', '阿木'),
     value = TRUE)
## [1] "\n"   "\r"   "阿木"

# 设置 perl = TRUE 后，'.'不能匹配出换行符（`\n`）
grep(
  pattern = '.',
  x = c('\n', '\r', '阿木'),
  value = TRUE,
  perl = TRUE
)
## [1] "\r"   "阿木"

# '^山.*月$'代表匹配山开头月结尾的字符串，.*表示任意长度任意字符
grep(pattern = '^山.*月$',
     x = c('山中明月', '山月', '牧月'),
     value = TRUE)
## [1] "山中明月" "山月"

# '[山月]'代表匹配任意含有山或月字的字符串
grep(
  pattern = '[山月]',
  x = c('山中明月', '山月', '月山', '山', '月'),
  value = TRUE
)
## [1] "山中明月" "山月"     "月山"     "山"       "月"

# '(山).*(月)'代表匹配同时含有山、月的字符串，山月二字之间允许存在任意字符，但山一定在月前面
grep(
  pattern = '(山).*(月)',
  x = c('山中明月', '山月', '月山', '山', '月'),
  value = TRUE
)
## [1] "山中明月" "山月"
```

断言，分正向和反向，由于现行语言为从左至右阅读，所以正向就是从左至右匹配，反向就是从右至左匹配。需要注意的是，R 的正则表达式引擎（TRE）不支持下面四种断言规则，需要加上`perl = TRUE`参数才不会报错。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`(?=)`|正向肯定断言|`a(?=b)`匹配‘a’，但仅当‘a’后面跟着‘b’|
|`(?!)`|正向否定断言|`a(?!b)`匹配‘a’，但仅当‘a’后面不跟‘b’|
|`(?<=)`|反向肯定断言|`(?<=a)b`匹配‘b’，但仅当‘b’前面是‘a’|
|`(?<!)`|反向否定断言|`(?<!a)b`匹配‘b’，但仅当‘b’前面不是‘a’|


```r
my_vector <- c('山中明月', '西山月', '山西下月下西山', '海上仙月')

# '山(?=月)'代表从左至右匹配，山字后面紧跟月字
grep(
  pattern = '山(?=月)',
  x = my_vector,
  value = TRUE,
  perl = TRUE
)
## [1] "西山月"

# '山(?!月)'代表从左至右匹配，山字后面不紧跟月字
grep(
  pattern = '山(?!月)',
  x = my_vector,
  value = TRUE,
  perl = TRUE
)
## [1] "山中明月"       "山西下月下西山"

# '(?<=山)月'代表从右至左匹配，月字前面紧跟山字
grep(
  pattern = '(?<=山)月',
  x = my_vector,
  value = TRUE,
  perl = TRUE
)
## [1] "西山月"

# '(?<!山)月'代表从右至左匹配，月字前面不紧跟山字
grep(
  pattern = '(?<!山)月',
  x = my_vector,
  value = TRUE,
  perl = TRUE
)
## [1] "山中明月"       "山西下月下西山" "海上仙月"
```

## 3. 限定符

限定符，用于控制模式匹配的次数。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`*`|匹配前面的子表达式零次或多次|等同于`{0,}`|
|`?`|匹配前面的子表达式零次或一次|等同于`{0,1}`|
|`+`|匹配前面的子表达式一次或多次|等同于`{1,}`|
|`{n}`|匹配前面的子表达式连续 n 次||
|`{n,}`|匹配前面的子表达式至少连续 n 次||
|`{n,m}`|匹配前面的子表达式，最少连续 n 次且最多连续 m 次，n 小于 m||


```r
my_vector <- c("a", "aa", "aaa", "b", "aba", "ababa", 'abababa')

# "a+"表示匹配的 a 至少有1个
grep(pattern = "a+", x = my_vector, value = TRUE)
## [1] "a"       "aa"      "aaa"     "aba"     "ababa"   "abababa"

# "a?"表示匹配的 a 至少有0个
grep(pattern = "a?", x = my_vector, value = TRUE)
## [1] "a"       "aa"      "aaa"     "b"       "aba"     "ababa"   "abababa"

# "a{2}"表示匹配连续2个 a
grep(pattern = "a{2}", x = my_vector, value = TRUE)
## [1] "aa"  "aaa"

# "(.*a.*){2,}"表示匹配2个 a，且 a 前后可以存在任意字符
grep(pattern = "(.*a.*){2,}", x = my_vector, value = TRUE)
## [1] "aa"      "aaa"     "aba"     "ababa"   "abababa"

# "(.*a.*){3,4}"表示匹配3到4个a,且 a 前后可以存在任意字符
grep(pattern = "(.*a.*){3,4}", x = my_vector, value = TRUE)
## [1] "aaa"     "ababa"   "abababa"
```

## 4. 预定义字符

预定义字符，就是预先定义好的一类字符。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`\\d`|匹配任意一个数字|d 代表 digit，等同于`[0-9]`|
|`\\D`|匹配任意一个非数字|等同于`[^0-9]`|
|`\\w`|匹配任意一个字母、数字或下划线|w 代表 word，等同于`[a-zA-Z0-9_]`|
|`\\W`|匹配任意一个非字母、数字或下划线|等同于`[^a-zA-Z0-9_]`|
|`\\s`|匹配任何空白符|s 代表 space，包括空格（` `）、制表符（`\t`）、换行符（`\n`）、回车符（`\r`）、换页符（`\f`）、垂直制表符（`\v`），等同于`[ \t\n\r\f\v]`|
|`\\S`|匹配任何非空白符|等同于`[^ \t\n\r\f\v]`|


```r
my_vector <- c('abc', 'ABC', '20240912', '2024_a', ' ', "❤")

grep(pattern = "\\d", x = my_vector, value = TRUE)
## [1] "20240912" "2024_a"
grep(pattern = "\\D", x = my_vector, value = TRUE)
## [1] "abc"    "ABC"    "2024_a" " "      "❤"
grep(pattern = "\\w", x = my_vector, value = TRUE)
## [1] "abc"      "ABC"      "20240912" "2024_a"
grep(pattern = "\\W", x = my_vector, value = TRUE)
## [1] " " "❤"
grep(pattern = "\\s", x = my_vector, value = TRUE)
## [1] " "
grep(pattern = "\\S", x = my_vector, value = TRUE)
## [1] "abc"      "ABC"      "20240912" "2024_a"   "❤"
```

单词字符通常是指字母、数字或下划线，那么单词字符之间存在边界的含义有两种情况，一是单词字符之间存在空格，二是单词字符在字符串的开头或结尾。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`\\b`|匹配单词边界|b 代表 boundary，匹配的模式在字符串中一个英文单词的开头或结尾|
|`\\B`|匹配非单词边界|与`\\b`含义相反，匹配的模式不在字符串中一个英文单词的开头或结尾|


```r
my_vector2 <- c("hello word", "word dog", "木word", '_word', "word木", "木word木")

# "word" 表示包含 word 的字符串
grep(pattern = "word", x = my_vector2, value = TRUE)
## [1] "hello word" "word dog"   "木word"     "_word"      "word木"    
## [6] "木word木"

# "\\bword" 表示 word 出现在英文单词的开头
grep(pattern = "\\bword", x = my_vector2, value = TRUE)
## [1] "hello word" "word dog"   "word木"

# "word\\b" 表示 word 出现在英文单词的结尾
grep(pattern = "word\\b", x = my_vector2, value = TRUE)
## [1] "hello word" "word dog"   "木word"     "_word"

# "\\bword\\b" 表示字符串中有独立的 word
grep(pattern = "\\bword\\b", x = my_vector2, value = TRUE)
## [1] "hello word" "word dog"

# "\\Bword" 表示 word 前面紧连接非单词边界
grep(pattern = "\\Bword", x = my_vector2, value = TRUE)
## [1] "木word"   "_word"    "木word木"

# "\\Bword" 表示 word 后面紧连接非单词边界
grep(pattern = "word\\B", x = my_vector2, value = TRUE)
## [1] "word木"   "木word木"

# "\\Bword\\B"表示 word 前后紧连接非单词边界
grep(pattern = "\\Bword\\B", x = my_vector2, value = TRUE)
## [1] "木word木"
```

## 5. 捕获与引用

前面提到`()`除了表示匹配还能捕获匹配成功的子字符串，这里捕获的意义在于捕获后能够二次引用。

|符号|释义|例子或说明|
|:----:|:----:|:----:|
|`()\\1`|对第一个捕获组的引用|比如`(\\d)`表示匹配并捕获任意一个数字，那么`(\\d)\\1`表示捕获的数字要重复一次，整体上需要捕获重复两次的数字|
|`()()\\2`|对第二个捕获组的引用|`()()\\2`表示在前两个括号中的模式匹配成功后，第二个括号捕获的内容需要再重复一次|
|`(?:)`|仅分组匹配而不捕获子表达式|不捕获子表达式就不能进一步引用|


```r
# '(\\d)\\1'代表匹配重复两次的数字
grep(pattern = '(\\d)\\1',
     x = c('11a', '22b', '3c'),
     value = T)
## [1] "11a" "22b"

# '(\\d)(\\d)\\2'代表匹配两个任意数字，并且第二个数字重复两次
grep(
  pattern = '(\\d)(\\d)\\2',
  x = c('2011a', '211a', '221b'),
  value = TRUE,
  perl = TRUE
)
## [1] "2011a" "211a"
```

## 6. 符号的优先级

|优先级|符号|释义|
|:----:|:----:|:----:|
|最高|`\`|转义符|
|高|`()`、`(?:)`、`(?=)`、`[]`|圆括号和方括号|
|中|`*`、`+`、`?`、`{n}`、`{n,}`、`{n,m}`|大多数元字符，限定符|
|低|`^`、`$`、预定义字符、普通字符|-|
|次最低|串接|即相邻字符连接在一起|
|最低|`|`|或|
