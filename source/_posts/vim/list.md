---
title: VIM递增列表实现
date: 2026-05-03 16:10:12
tags: VIM
categories: VIM
---

有时候需要在VIM中生成递增列表，如数据库递增主键。一般我们可通过excel表格生成，在拼接需要的字符串。这里介绍VIM递增列表实现。

### 使用`put`和`range`快速生成数字

```vim
:put=range(1,5)
```

输出如下:

```
1
2
3
4
5
```

通过控制增量，可以生成降序列表。

```vim
:put=range(5,0,-1)
```

我们可以使用`line('.')`显示当前行号，结合`put/range`生成列表。如需生成当前行到第20行的行号，可以执行以下操作：

```vim
put=range(line('.'), 20) ; 
```

### 快速增加数字列

假设我们有一列数字，比如下面html中的0：

```html
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
<div class="test">0</div>
```

如果我们想增加所有的零(1,2,3,...)，方法如下：

1. 使用VISUAL BLOCK模式(`Ctrl+v`)，选中所有的零
2. 执行`g Ctrl+a`你将得到如下结果

```html
<div class="test">1</div>
<div class="test">2</div>
<div class="test">3</div>
<div class="test">4</div>
<div class="test">5</div>
<div class="test">6</div>
<div class="test">7</div>
<div class="test">8</div>
<div class="test">9</div>
<div class="test">10</div>
```

VIM8具有使用`<c-a>`自动递增数字(使用`<c-x>`递减)的功能。你可以通过`:help CTRL-A`来检查它。我们还可以通过前面插入一个数字来更改增量。如果我们想要10,20,30,...请改为执行`10g <c-a>`。
