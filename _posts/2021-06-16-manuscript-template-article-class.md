---
layout: post
title: Manuscript template using article class
author: Rangsiman Ketkaew
date: "2021-06-16 14:06:00 +0200"
category:
  - LaTeX
summary: Manuscript template using article class
thumbnail: posts/LaTeX_logo.svg.png
permalink: content/27
comments: true
---

## Article class

Authors, emails, and affiliations are supported.

```tex
\documentclass[a4paper]{article}

\newcommand{\affilmark}[1]{\rlap{\textsuperscript{\itshape#1}}}
\usepackage{lipsum}

\begin{document}

\vspace*{3ex}
\begin{center}\LARGE
  The title of this paper, long enough to break over two lines
\end{center}
\vspace*{2ex}
\begin{flushleft}\large
A. N. Author\affilmark{a},\quad
B. P. Another\affilmark{b},\quad
C. Q. Third\affilmark{c}\\[2ex]
\normalsize\itshape
\textsuperscript{a,b}\,Department of Cuisine, University of Nowhere\\
\textsuperscript{c}\,Department of Departmentalization, University of Somewhere\\[1ex]
\upshape Corresponding author's email: \texttt{A.N.Author@nowhere.edu}
\end{flushleft}
\vspace*{3ex}

\begin{abstract}
\lipsum[1-2]
\end{abstract}

\section{Introduction}
\lipsum
\end{document}
```

Ref: [https://tex.stackexchange.com/a/28385/117615](https://tex.stackexchange.com/a/28385/117615)
