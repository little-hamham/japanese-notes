# 日语笔记 LaTeX 版

这套模板基于之前写的数学讲义模板重新设计，适合用A4纸打印、
有些知识框和猎宝小表情，并增加了适合日语学习的专用命令。
因为是自用所以章节、小节及学习框默认不编号，适合直接用日期作为标题随手记录。
文末有其如果用于类似标日课程学习的预览效果。

## 文件

- `main.tex`：文档骨架和日期文件的 `\input` 清单。
- `sections/`：按日期存放笔记正文，例如 `2026.6.22.tex`。
- `japanese-notes.sty`：字体、颜色、封面和自定义环境。
- `latexmkrc`：固定使用 XeLaTeX，并把编译产物放入 `output`。
- `assets/silent`：猎宝的小表情包qwq（用GPT生成的）。

## 编译

在当前文件夹执行：

```powershell
latexmk main.tex
```

生成的 PDF 位于 `output/pdf/main.pdf`。手动编译时请使用 XeLaTeX：

```powershell
xelatex main.tex
xelatex main.tex
```

## 添加日期笔记

复制 `sections/202x.x.xx.tex` 并改成新的日期文件，然后在 `main.tex`
的日期清单中增加一行：

```latex
\input{sections/202x.x.xx.tex}
```

日期文件中只写 `\section` 和正文，不要重复导言区、
`\begin{document}` 或 `\end{document}`。

## 常用命令

```latex
\jp{日本語}
\furigana{漢字}{かんじ}
\silenticon{wink} % 可用 anger/cool/milk/shy/wink/wipe

\begin{vocab}{主题}
  \vocabentry{単語}{たんご}{名词}{单词}
\end{vocab}

\begin{grammar}{A は B です \level{N5}}
  语法说明。
\end{grammar}

\begin{example}
  \sentence{日本語を勉強します。}
    {にほんご を べんきょう します。}
    {学习日语。}
\end{example}
```

模板使用 TeX Live 自带的 IPAex 日文字体，不依赖额外图片或系统日文字体。
猎宝小表情会自动出现在常用学习框标题中，也可通过 `\silenticon{表情名}` 单独调用。
