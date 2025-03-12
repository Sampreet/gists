# Best Practices for $\LaTeX$ Manuscripts

> A gist of habits to write cleaner and easy-to-understand $\LaTeX$ sources for manuscripts.

## Document Class, Packages and Bibliography Styles

Before preparing a manuscript, it is recommended to go through the preparation guidelines for the journal where the manuscript is to be submitted.
Every publication house has its own document class and require the manuscript to be formatted as per the style guide of the journal.
Some of these document classes require additional style files and the TeX distribution needs to be configured accordingly.
The distribution might also download some additional packages to fulfil the requirements of the document class.

***Note:*** Although most journals accept manuscripts formatted in the default `article` document class, following the journal's style guide speeds up the correspondence process.

*A* $\LaTeX$ *template using the `article` class can be found in the [Article Template for LaTeX](../../../snippets/languages/latex/latex-article-template.md) snippet.*

***Note:*** A comprehensive list of documented classes can be found in the [CTAN Archive](https://ctan.org/topic/class).

Along with the style guide for text, math, figures and tables, the manuscript templates containing the instructions for authors usually mention the packages and bibliography styles that can be used with for each document class.
Some key points to keep in mind for the `\usepackage{}` command are:
*   Not every document class is compatible with every package and only ***supported packages*** should be used.
    For example, the `iopart` class does not support the `amsmath` package and one need to use the `iopams` package instead.
*   Only the ***necessary packages*** should be used in order to avoid conflicts between commands.
    Keeping the number of packages used to minimum also reduces the compilation times.
    Usually, the packages `garphicx` and `amsmath` (optionally with `cite`, `hyperref` and `color`) suffices the requirements for most manuscripts in Physics.

***Note:*** Although at times, the manuscript might compile with an incompatible package, but a small conflict may trigger a large number of compilation errors which can sometimes be very confusing to debug.

*More information on individual packages can be found in the [Common LaTeX Packages](./latex-common-packages.md) tutorial.*

The `\bibliographystyle{}` command should be used to format the references as per the journal-specific guidelines.

A table of common publication houses for Physics is given below:

Publication House | Document Class | Bibliography Style | Links | 
--- | --- | --- | --- |
American Physical Society (APS) | `revtex4-2` | `apsrev4-2` | [Information for Authors](https://journals.aps.org/authors) |
Institute of Physics (IOP) | `iopart` | `iopart-num` | [LaTeX Template](https://publishingsupport.iopscience.iop.org/questions/latex-template/) |
Optica (OSA) | `optica-article` | `opticajnl` | [Journal Style Guide](https://opg.optica.org/submit/style/osa-styleguide.cfm) |

## Indentations and Line Breaks

Although $\LaTeX$ does not consider indentations, it is easy to differentiate blocks of sections, figures and equations when the corresponding inner blocks are indented.
For example,
```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.48\textwidth]{sample.png}
    \caption{
        This is a sample figure.
        It's caption contains multiple lines.
        Hence this block is indented for clarity.
    }
    \label{fig:sample}
\end{figure}
```

Indentation and line breaks can also be followed for paragraphs.
A single line break compiles to a space.
A double line break denotes a change in the paragraph.
A single line break after an equation does not indent the text and the `\noindent` command can be avoided.
Key advantages of indentation and line breaks in text are:
*   Errors can be quickly indentified by looking at the line number in the compilation output.
*   Indented blocks can be minimized and maximized easily in most code editors, making the document compact and easier to handle.

An example of indented text block with line breaks is:
```latex
1   \section{Introduction}
2       \label{sec:intro}
3       Welcome to the introduction for this manuscript.
4       In this paragraph, we detail on the definition and related works for the major phenomena addressed by our work.
5       This \line will give a compilation error but can be identified quickly by the line number.
6       We will also discuss the novelty of our work and it applications.
7
8       This is a new paragraph.
9       Here, we will mention the structure of the manuscript.
```

***Note:*** Sections can also be separted visually using the comment (`%`) blocks.
For example,
```latex
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%         INTRODUCTION         %%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```

## Labelling and Cross-referencing Items

Sections, equations, figures and tables should be appropriately labelled.
The convention of labelling is individual-dependent.
However, a consistent convention across all manuscripts is commendable.
The `\label{}` command takes non-spaced names and the corresponding item can be referenced using the `\ref{}` command.
Advantages of labelling and cross-referencing using those labels are:
*   Automatic update of item numbers within the text when additions and deletions are made in between.
    This eliminates a lot of hastle and mitigates error specially while referencing equations.
*   Ability to reference the item multiple times within the text without having to cross-check.
*   Since every label has to be unique to avoid compilation errors, there is no overlap in the numbering.

It is also pereferable to add an identifier for the *type* of item denoted by the label.
For example, section labels may carry a prefix `sec:`, equations `eqn:`, figures `fig:` and tables `tab:`.
Subsections, subsubsections and child items may inherit the parent label with an additional identifier suffix.
This makes it easier to keep track of the sections in which the corresponding items exist.
For example,
```latex
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
```

## Equations and Symbols

While writing equations, specially long ones, it is advisable to adhere to the following conventions:
*   *Proper spacing:* To avoid merging two or more variables by mistake, individual variables should be separated by spaces.
    Spacing also provides ease in demarcating the variables while reading the expression.
*   *Brackets:* Instead of using the `()`, `\{\}` and `[]` brackets directly, the `\left` and `\right` commands should be prefixed for them.
    For angular brackets, `\langle` and `\rangle` should be used.
    These commands also automatically adjust the size of the brackets to enclose the inner expressions.
    For example, $\left( \frac{1}{\frac{\kappa}{2}} \right)$ against $( \frac{1}{\frac{\kappa}{2}} )$.
*   *Multiline equations:* The `eqnarray` block can be used with the `\nonumber` command to break an equation into multiple lines.
    For line breaks between brackets, the commands `\Big`, `\Bigg`, etc. should be used instead of `\left` and `\right`.
*   *Multiple equations:* To write a coupled set of equations in a single line, the command `\quad` can be used to separate the individual equations.
    Else, the `eqnarray` block can be used to write multiple equations.
    To denote the equations by a single number, the `subequations` block should be used on top of `eqnarray`.

An example of formatted equation is:
```latex
\begin{subequations}
    \begin{eqnarray}
        \label{eqn:first}
        x_{i + 1} & = & a x_{i} + \left( \frac{b^{2} + 2}{a} \right) x_{i - 1} \\
        \label{eqn:second_third}
        y_{i + 1} & = & a x_{i} y_{i} \quad y_{i + 1}^{\prime} = y_{i + 1} + 1 \\
        \label{eqn:fourth}
        z_{i + 1} & = & d y_{i - 1} z_{i}^{x_{i}} \nonumber \\
        && + 2 x_{i} z_{i - 1}
    \end{eqnarray}
\end{subequations}
```

A list of supported symbols in $\LaTeX$ can be found in [Overleaf's documentation](https://www.overleaf.com/learn/latex/List_of_Greek_letters_and_math_symbols).
Care should be taken while writing standard symbols.
For example, `\Re` and `\Im` should be used instead of `Re` and `Im` for real and imaginary components, `\prime` instead of `'`, `\times` instead of `X`, etc.

## Coloring and Version Control

A suitable way to mark the changes in a multi-author manuscript is by the use of different colors by different authors using the `color` package.
Once the edits have been discussed and agreed upon after a specific milestone, the colors can be removed and the procedure can be repeated till the manuscript is finalized.

Here, versioning and saving a snapshot of the manuscript after each milestone can be helpful in case some changes need to be reverted at a later instance of time.
Version control systems (VCS) like `Git` and `Mercurial` can be used to do so.
Another advantage of maintaining a VCS for collaborative projects is that no change is missed even though the author might have forgotten to color the change.

## Further Structuring

As the length of the manuscript grows, it gets increasingly time-taking to scroll through the sections over and over again.
Although most IDEs feature detection of position by clicking on the PDF, one has to still scroll through the PDF.
A better way to write long manuscripts is by structuring the contents into folders and files and then using the `\input{}` command to compile them together.
For example, the folder structure can be:
```
manuscript/
│
│───images/
│   │
│   ├───system_dynamics.png
│   ├───system_model.png
│   └───...
│
│───sections/
│   │
│   ├───system.tex
│   ├───system_dynamics.tex
│   ├───system_model.tex
│   ├───system_model_parameters.tex
│   └───...
│   
├───manuscript.tex
└───references.bib
```
The `manuscript.tex` file may then contain the blocks:
```latex
\section{System}
    \label{sec:system}
    \input{system.tex}

    \subsection{Model}
        \label{sec:system_model}
        \input{system_model.tex}

        \subsubsection{Parameters}
            \label{sec:system_model_parameters}
            \input{system_model_parameters.tex}

    \subsection{Dynamics}
        \label{sec:system_dynamics}
        \input{system_dynamics.tex}
```
This not only removes the need for scrolling, but also gives a cleaner look to the manuscript.