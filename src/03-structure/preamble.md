# Preambolo e corpo

Un sorgente LaTeX si compone di due parti: la prima chiamata *preambolo* ospita
il codice che definisce la *classe* del documento, il caricamento di pacchetti
d'estensione e altre possibili impostazioni.

Nel preambolo non è ammesso alcun materiale da comporre sulla pagina, per
esempio del testo. Questo sarà contenuto nella seconda parte del sorgente detto
*corpo*.

Questa partizione è riconoscibile in questo sorgente:

```latex
\documentclass{article}
\usepackage[italian]{babel}
\usepackage{booktabs}

\usepackage{siunitx}
\sisetup{output-decimal-marker={,}}

\usepackage{graphicx}

\begin{document}
Corpo del documento.

Il testo del documento va qui.
\end{document}
```

Prima cosa da fare è definire il tipo di documento specificando una *classe*.
Una classe stabilisce tutta una serie di impostazioni che caratterizzano
l'aspetto tipografico del documento, a seconda della sua specifica tipologia.

Esiste un insieme predefinito di classi LaTeX, in particolare le tre seguenti:

- article
- report
- book

Nel preambolo possiamo inserire righe bianche per separare il codice, caricare
pacchetti anche se non verranno utilizzati, e lasciare commenti per ricordarci
qualcosa da completare o 
