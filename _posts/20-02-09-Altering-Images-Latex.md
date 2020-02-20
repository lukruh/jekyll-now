---
layout: post
title: Fix Shifting of Alterning Images in Latex Beamer Class
tags: latex,beamer,layout,presentation,trick
sources:
  - https://stackoverflow.com/a/26189728/7268121
---

Using the Latex Beamer class to create presentations, is a good idea to create clean, compatible, scientific presentations. Now or than tiny hurdles can ruin drive you crazy, when you don't know how to fix them.  One of these is the small but noticeable shift of altering images in one slide, caused by ordinary spaces or linebreaks. The following shows the issue and how to fix it.



## Example


```latex
\begin{frame}{Linear Regression \headlogo}
    \begin{figure}
      \includegraphics<1>[width=0.8\textwidth]{img/regression1}
      \includegraphics<2>[width=0.8\textwidth]{img/regression2}
      \includegraphics<3>[width=0.8\textwidth]{img/regression3}
      \caption{Example data with arbitary units (linear function with gauss distributed noise)}
    \end{figure}
  \end{frame}
```

![Shifted Images](/images/shifted.gif)

## Solution

The space between the alternating figures are generated, when the pdf is rendered. Probably there are some line breaks, spaces or tabs in the code that cause this problem. To keep the readability of the code, one can simply end the sensitive with comments, to make sure the line breaks are ignored correctly.

```latex
\begin{frame}{Linear Regression \headlogo}
    \begin{figure}%
      \includegraphics<1>[width=0.8\textwidth]{img/regression1}%
      \includegraphics<2>[width=0.8\textwidth]{img/regression2}%
      \includegraphics<3>[width=0.8\textwidth]{img/regression3}%
      \caption{Example data with arbitary units (linear function with gauss distributed noise)}%
    \end{figure}
  \end{frame}
```

![Fixed Images](/images/fixed.gif)