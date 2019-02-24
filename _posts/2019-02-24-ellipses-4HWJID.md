---
title: 4HWJID
permalink: 4HWJID
layout: post
date: 2019-02-24 19:04:10
category: ellipses
---

```latex
% Dans le préambule
% -----------------
\usepackage{pst-circ}
% -----------------

\begin{pspicture}(0,0)(4.5,3)
\pnodes(0,0){M}(0,2){N}(4,2){P}(4,0){Q}
\switch(P)(Q){}
\resistor[parallel,labeloffset=0](P)(Q){$R$}
\capacitor(M)(Q){$C$}
\vac(M)(N){$E$}
\coil[tensionlabel={$u_L$}](N)(P){$L$}
\end{pspicture}
```