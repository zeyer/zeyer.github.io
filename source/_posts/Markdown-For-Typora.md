---
title: Markdown for Typora
tags: start
---


## 概述

**Markdown**是由[Daring Fireball](http://daringfireball.net/)的创造的一种语法，它原始的指导手册见[此处](http://daringfireball.net/projects/markdown/syntax).但对于不同的语法解析器和编辑器而言，它的语法存在差异。**Typora**采用了Github Flavored Markdown(GFM),但仍然和其他编辑器有所不同。

## 块元素

### 段落和空行

段落是一行或多行连续的文本构成的。在markdown源代码中，段落被更多空行分隔。而在**Typora**中，只需要点击`回车`按钮就可以创建一个新的段落。而`</br>`是不被支持的。

### 标题

标题一共有1-6六个等级，用`#`符号的个数来表示标题的级别，1个`#`表示一级标题，2个`#`表示二级标题，以此类推，6个`#`表示六级标题。例子如下：

```markdown
# 这是一级标题

## 这是二级标题

###### 这是六级标题
```

在Typora中，`#`后直接输入内容，按 `回车` 键创建一个标题。

### 引用

Markdown文档中用 `>` 来表示引用块，用法示例：

```markdown
> 这是一个两段文字的引用。这是第一段
>
> 这是第二段文字。。。。。。



> 这是另一个引用，这个应用只有一段文字。两段引用之间用三个空行分开。
```

在Typora中，直接在 `>` 后输入应用内容，就可以生成引用。

Typora会自动为你插入换行符。同时块引用之中可以内嵌子引用。

### 列表

输入`* 列表内容` 将会生成一个无序列表，其中`*` 可以被 `+` 或者`-` 代替。

输入  `1. list item 1` 将会创建一个有序列表，两种创建方法的markdown源代码如下：

```markdown
## un-ordered list
*   Red
*   Green
*   Blue

## ordered list
1. Red
2. Green
3. Blue
```

### 任务列表

任务列表是被标记已完成或者未完成的列表项，通常用[ ] 或者 [ x] 来表示。用例如下：

```markdown
- [ ] 一个任务列表
- [ ] 列表语法
- [ ] 未完成
- [X] 已完成
```

你可以通过点击列表前的复选框来改变完成状态或者未完成状态。

### 代码块

Typora只支持Github Flavored Markdown格式的fences.markdown中的原生代码块是不被支持的。

用代码块是很容易的，输入 \`\`\` 然后点击`回车` 。添加一种语言标记在\`\`\` 后面，然后将会使用该种语言的语法高亮。

### 数学公式

你可以使用**MathJax**提交*LaTex* 数学表达。

输入 $$，然后点击`回车`键，将会触发一个输入区域，该输入区域支持*Tex/LaTex*，直接输入公式代码即可。以下是使用实例：

在markdown源文件中，数学公式块是被`$$`所包含的：
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$


```markdown
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
```

但是在Hexo博客中，由于未原生支持MathJax，虽然可以用[Hexo MathJax插件](https://unnamed42.github.io/2015-12-02-Hexo-MathJax%E6%8F%92%E4%BB%B6.html#介绍)解决，但是，LaTeX包含大量的像\这样的特殊字符，这就给手动转义带来了极大的不便（如上述代码块中第3行和第四行末尾）。这种情况下，你可以使用 hexo-math 的标签来让你解脱。只需要将`$$`换成如下的hexo math标签即可。tag具体用法如下：

```markdown
{% math %}
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
{% endmath %}
```



### 表格

输入`| 标题1  | 标题2 |`  然后点击 `回车` 键就可以创建一个包含两列的表格。

在表格被创建后，可以看到表格上有工具栏，可以利用工具栏重新设置行列数、对齐方式或者删除表格

下面这些操作可以跳过，因为通过Typora自动生成的表格包括了这些设置的可视化操作。

在markdown源代码中，表格是这样的

``` markdown
| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |
```

同时，对于表格的内容可以设置链接，加粗，斜体或者删除线等等。

最后，通过在标题行使用标点符号`:`  ，可以设置对齐方式

``` markdown
| 左对齐  | 居中 | 右对齐 |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
```

标点符号`:`在最左边表示左对齐，标点符号`:`在最右边表示右对齐，左右两边都有标点符号`:`表示居中。

### 脚注

```markdown
你可以用这样的方式创建一个脚注 [^脚注]。
[^脚注]: 这是一个脚注内容。
```

最终产生的效果如下：

你可以用这样的方式创建一个脚注 [^脚注]。
[^脚注]: 这是一个脚注。

鼠标悬浮在`脚注`两个字上时，会显示具体内容。

### 水平线

在一个空行中输入`***`或者 `---` ，然后点击`回车`将会生成一条水平线。

---

### YAML Front Matters

Typora支持 [YAML Front Matters](http://jekyllrb.com/docs/frontmatter/) 。在文章的顶部输入`---` 然后按下`回车` 键，将会创建一个。 