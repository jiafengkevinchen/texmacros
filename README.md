# LaTeX macros

Add the following bash script to `~/.bash_profile` to get terminal commands for fast initiation of new LaTeX documents.

```bash
alias gettexmacros="curl -L https://raw.githubusercontent.com/jiafengkevinchen/texmacros/master/macros.sty > macros.sty"

function newdocument() {
    local filename=${1:-main};
    curl -L "https://raw.githubusercontent.com/jiafengkevinchen/texmacros/master/macros.sty" > macros.sty;

    echo '\\\documentclass[11pt, reqno]{amsart}
\\\usepackage{macros}

\\\begin{document}

\\\end{document}" > $filename.tex; subl $filename.tex;
}

alias newdoc="newdocument"
```

Usage: `$ gettexmacros` or `newdoc [filename]` (default is `main.tex`)
