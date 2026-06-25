# Pacchetti

Il linguaggio di markup di LaTeX si compone di comandi e ambienti di uso
generale. Comporre una tabella, un elenco numerato per esempio. Ma un documento
può contenere gli oggetti più svariati: il grafico di dati sperimentali, codici
a barre, tabelle multipagina, eccetera eccetera.

Qualsiasi cosa sia è probabile che esista un pacchetto in grado di comporlo e se
non esiste possiamo sempre scriverlo noi.

Possiamo classificare i *pacchetti d'estensione* a seconda del loro scopo:

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
