# Article Template for LaTeX

## General

```latex
\documentclass[a4paper, 11pt]{article}
% custom layout
\usepackage[a4paper, width=160mm, top=32mm, bottom=32mm]{geometry}
% figures and sub-figures with captions
\usepackage{graphicx}
\usepackage{wrapfig}
\usepackage{subcaption}
% appendix formatting
\usepackage[title, titletoc]{appendix}
% math fonts
\usepackage{amssymb, amsmath, amsfonts}
% underlining and striking out
\usepackage{ulem}
% headers and footers
\usepackage{fancyhdr}

% path to images
\graphicspath{{images/}}
% bibliography options
\bibliographystyle{plain}

% fancyhdr options
\pagestyle{fancy}
\setlength{\headheight}{16pt}
% header
\fancyhead{}
\fancyhead[R]{\leftmark}
% footer
\fancyfoot{}
\fancyfoot[L]{\textit{Title}}
\fancyfoot[R]{\thepage}

\begin{document}
    \title{Title}
    \author{Name}
    \maketitle

    \tableofcontents

    \section{New Section}
        \subsection{New Sub-section}
    
\end{document}
```