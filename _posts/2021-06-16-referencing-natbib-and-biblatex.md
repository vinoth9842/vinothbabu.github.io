---
layout: post
title: Referencing with natbib and biblatex
author: Rangsiman Ketkaew
date: "2021-06-16 14:23:00 +0200"
category:
  - LaTeX
summary: Referencing with natbib and biblatex
thumbnail: posts/LaTeX_logo.svg.png
permalink: content/28
comments: true
---

- [Natbib](#natbib)
- [Biblatex](#biblatex)

## Natbib

```tex
\documentclass[12pt,a4paper]{article}
\usepackage[english]{babel}
\addto{\captionsenglish}{
  \renewcommand{\bibname}{References}
}
\usepackage[utf8]{inputenc}

\usepackage[sort&compress,numbers]{natbib}

\begin{document}

...
\bibliographystyle{unsrtnat}
\bibliography{main}

\end{document}
```

You can embed reference sources into the main.tex file by compiling the pdf first. Then copy the whole content from \*.bbl from and replace bibligraphy commend, like this:

```tex
\begin{document}

...
\begin{thebibliography}{9}
\bibitem{latexcompanion}
Michel Goossens, Frank Mittelbach, and Alexander Samarin.
\textit{The \LaTeX\ Companion}.
Addison-Wesley, Reading, Massachusetts, 1993.

\bibitem{einstein}
Albert Einstein.
\textit{Zur Elektrodynamik bewegter K{\"o}rper}. (German)
[\textit{On the electrodynamics of moving bodies}].
Annalen der Physik, 322(10):891–921, 1905.

\bibitem{knuthwebsite}
Knuth: Computers and Typesetting,
\\\texttt{http://www-cs-faculty.stanford.edu/\~{}uno/abcde.html}
\end{thebibliography}

\end{document}
```

## Biblatex

```tex
\usepackage[
backend=biber,
style=numeric-comp,
citestyle=nature
]{biblatex}
\addbibresource{main.bib}

\begin{document}

...

\printbibliography

\end{document}
```

You can also rename the reference section from "References" to, e.g., "Sources":

```tex
\begin{document}

...

\printbibliography[title={Sources},prenote=note]

\end{document}
```
