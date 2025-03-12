# Article Template for $\LaTeX$

## Barebones

```latex
\documentclass[a4paper, 11pt]{article}
% custom layout
\usepackage[a4paper, width=160mm, top=32mm, bottom=32mm]{geometry}
% figures
\usepackage{graphicx}
% % uncomment to support word wrap around figure
% \usepackage{wrapfig}
% % uncomment for subcaption
% \usepackage{subcaption}
% % uncomment to add appendix to table of contents
% \usepackage[title, titletoc]{appendix}
% math fonts
\usepackage{amsmath}
% % uncomment for more fonts and symbols
% \usepackage{amsfonts, amssymb}
% % uncomment to support underlining and striking out
% \usepackage{ulem}
% % uncomment for author affiliation
% \usepackage{authblk}

% % uncomment block to add headers and footers
% \usepackage{fancyhdr}
% % fancyhdr options
% \pagestyle{fancy}
% \setlength{\headheight}{16pt}
% % header
% \fancyhead{}
% \fancyhead[R]{\leftmark}
% % footer
% \fancyfoot{}
% \fancyfoot[L]{\textit{Title}}
% \fancyfoot[R]{\thepage}

% path to images for structured
\graphicspath{{images/}}
% bibliography options
\bibliographystyle{plain}

\begin{document}
    % heading
    \title{Title}
    \author{Name}
    % % uncomment for affiliation along with the authblk package 
    % \affil{Affiliation}
    \date{\today}
    \maketitle

    % contents
    \tableofcontents
    
    % sections, equations, figures and tables
    \section{System}
        \label{sec:system}
        Motivation for the system...

        \subsection{Model}
            \label{sec:system_model}
            Description of the model...
            \begin{figure}[ht]
                \centering
                \includegraphics[width=0.48\textwidth]{system_model.png}
                \caption{Schematic diagram.}
                \label{fig:system_model}
            \end{figure}

            \subsubsection{Parameters}
                \label{sec:system_model_parameters}
                Meaning of the parameters...
                \begin{table}[h]
                    \centering
                    \begin{tabular}{c|l}
                        \textbf{Parameter} & \textbf{Physical meaning} \\
                        \hline
                        $\Delta$ & detuning parameter \\
                        ... & ... \\
                    \end{tabular}
                    \caption{Parameters and their physical meanings.}
                    \label{tab:system_model_parameters}
                \end{table}

        \subsection{Dynamics}
            \label{sec:system_dynamics}
            Derivation of the dynamics...
            \begin{eqnarray}
                \label{eqn:system_dynamics}
                \ddot{y} & = & a \dot{y} + b y + c \\
                \ddot{x} & = & d y + e x
            \end{eqnarray}
            \begin{figure}[ht]
                \centering
                \includegraphics[width=0.48\textwidth]{system_dynamics.png}
                \caption{Time evolution.}
                \label{fig:system_dynamics}
            \end{figure}

    % add bibliography
    \bibliography{references}
    
\end{document}
```