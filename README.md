# LaTeX macros

Add the following bash script to `~/.bash_profile` to get terminal commands for fast initiation of new LaTeX documents.

```bash
alias gettexmacros="curl -L https://raw.githubusercontent.com/jiafengkevinchen/texmacros/master/macros.sty > macros.sty; curl -L https://raw.githubusercontent.com/jiafengkevinchen/texmacros/master/localSettings.yaml > localSettings.yaml"

function newdocument() {
    local filename=${1:-main};
    curl -L "https://raw.githubusercontent.com/jiafengkevinchen/texmacros/master/macros.sty" > macros.sty;

    echo '% arara: indent: {overwrite: yes, modifylinebreaks: yes, settings: local, where: localSettings.yaml}
% arara: pdflatex
\documentclass[12pt]{article}
\usepackage{macros}

\begin{document}

\end{document}' > $filename.tex; subl $filename.tex;
}

alias newdoc="newdocument"
```

Usage: `$ gettexmacros` or `newdoc [filename]` (default is `main.tex`)
