# basic-beamer-template
Basic beamer/latex template for slides


## THEME
* Using `metropolis` theme -- https://github.com/matze/mtheme

* light/dark background:
```latex
% LIGHT THEME
\usecolortheme[snowy]{owl}

% DARK THEME
\usecolortheme[]{owl}
```

* More beamer (older) themes:
  https://hartwork.org/beamer-theme-matrix/


## Recipes

### Trimming images
```latex
  \includegraphics[width=\columnwidth, clip=true,trim=l b r t]{figs/fig}
```

### Background Images in slides:
  - includes translucid effect, which requires the `transparent` package
```latex
% Local background must be enclosed by curly braces for grouping.
{
%\usebackgroundtemplate{\transparent{0.45}\includegraphics[width=\paperwidth]{figs/mp_projs_02}}%
\usebackgroundtemplate{
%       \parbox[c][\paperheight][c]{\paperwidth}{\centering\tikz\node[opacity=0.5]{\centering\transparent{0.4}\includegraphics[width=\paperwidth]{figs/mp_projs_02}};}
        \parbox[c][\paperheight][c]{\paperwidth}{\centering\transparent{0.3}\includegraphics[width=\paperwidth]{figs/mp_projs_02}
                %\flushright\tiny Image: \url{https://cmsweb.utsc.utoronto.ca/marcelo-ponce/projects/}
        }
}
\begin{frame}
...
\end{frame}
}
```
  - OR, using `tikz`
```latex
{
\usebackgroundtemplate{
  \tikz\node[opacity=0.3] {\includegraphics[height=\paperheight,width=\paperwidth]{YOURfigure}};
  \tikz\node[opacity=0.3] {\includegraphics[height=\paperheight,width=0.45\paperwidth]{YOURotherFIG}};
\begin{frame}
...
\end{frame}

```


## Packages
* `listings` -- for including code in slides, see configuration in main wrapper
* `verbatim` -- for defining blocks of comments
