# Latex

## 文字、章节、引用

### 中文排版ctexart

```latex
\documentclass[UTF8]{ctexart}
\begin{document}

\end{document}
```

### 空格和分段

连续的若干空格会被认为是一个空格

行末的换行符被视为一个空格，但连续的两个换行符，会将文字分段

或者实用`\par`来分段

### 注释

% 表示注释

### 转义字符

`\verb||`

使用`\`来转义特殊字符

`\textbackslash`表示`\`

### 断行

`\\` or `\newline`用来断行

不会在段落之前产生空格

### 断页

`\newpage` - 双栏排版时，会把新页放置右栏

`\clearpage` - 直接新提一页

### 断词

自动生成

## 标题

章 - `\chapter{title}` - 只在 report 和 book 中有效

节 - `\section{title}`

小节 - `subsection{title}`

分块 - `\part` 不影响其他编号
