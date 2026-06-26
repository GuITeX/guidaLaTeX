# Primo documento

Proviamo a scrivere il semplice testo "Ciao mondo" su una pagina bianca. Per
prima cosa, serve un editor di testi. In teoria se ne può scegliere uno
qualsiasi. Bene, sceglietene uno e create un file di testo dal nome
`primodocumento.tex`.

> [!NOTE]
> la distribuzione TeX Live comprende l'editor [TeXworks](https://tug.org/texworks/)
> semplicissimo da usare

Adesso copiate nel file queste righe di codice:

```latex
\documentclass{article}
\begin{document}
Ciao mondo.
\end{document}
```

Queste quattro semplici righe di codice istruiscono il compositore a

* creare un documento di uno stile predefinito, in questo caso la classe
  article, ma ce ne sono tanti altri i cui dettagli possono essere approfonditi
  in un secondo momento
* iniziare un documento `\begin{document}`
* stampare la stringa `Ciao mondo.`
* terminare il documento `\end{document}`

Il linguaggio che si usa nei sorgenti LaTeX è un linguaggio di markup: le
informazioni che servono a comporre i documenti sono "marcate" da appositi
comandi.

Ecco il risultato della compilazione del vostro primo sorgente:
[primodocumento.pdf](images/primodocumento.pdf).

Facile!
