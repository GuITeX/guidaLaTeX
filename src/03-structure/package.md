# Pacchetti

TeX prevede che si possano programmare nuove funzioni. LaTeX stesso ne è un
esempio che a sua volta prevede la possibilità di scrivere *pacchetti
d'estensione*. I pacchetti sono la ricchezza di LaTeX. Un patrimonio di migliaia
di nuove possibilità compositive e funzioni.

Possiamo classificarli a seconda dello scopo:

- impostazioni del documento: font, gabbia del testo, ...
- composizione del testo in una data lingua: regole di cesura a fin di riga,
  convenzioni tipografiche, documenti multilingua, ...
- potenziamento del linguaggio LaTeX di base: sommari complessi, matematica
  avanzata, ...
- composizione di oggetti tipografici speciali: unità di misura, poesie in
  versi, una partita a scacchi, ...

I pacchetti si caricano escusivamente nel preambolo con il comando
`\usepackage{}`.

La sintassi è la seguente:

```latex
\usepackage[opzioni]{nome-pacchetto}
```

## Pacchetti di uso comune

Per diverse ragioni ci sono funzioni essenziali che non appartengono al nucleo
di LaTeX. Per citarne una l'inclusione di immagini. A ciò rimediano i pacchetti
di uso comune. Eccone un elenco:

- `babel` compatibile con LuaLaTeX, è il pacchetto di eccellenza per consentire
  al compositore di assumere le regole tipografiche specifiche per una lingua.

- `graphicx`
- `tikz`
- `xcolor`

- `caption`
- `float`
- `subfig`

- `paralist`
- `enumitem`
- `booktabs`

- `hyperref`

- `geometry`
- `fancyhdr`
- `emptypage`
- `fancyverb`
