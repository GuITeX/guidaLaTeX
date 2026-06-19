# Compilare il sorgente

I programmi TeX sono a riga di comando. Compilare un sorgente significa eseguire
il compositore in un terminale passandogli il nome del file.

![Schema di input/output: la compilazione del sorgente](images/compile-latex.svg)

Il comando va dato scrivendo il nome del compositore, per esempio `lualatex`,
seguito da uno spazio e dal nome del file con o senza estensione. Terminata la
digitazione del comando si preme il tasto invio per eseguirlo.

```bash
lualatex primodocumento.tex
```

Quello riportato è il comando di compilazione del sorgente del capitolo
precedente della guida.

## Compilare con TeXworks

Gli editor di testo dedicati a LaTeX hanno molte facilitazioni tra cui la
compilazione con un click. Di più, spesso il PDF è mostrato a fianco del testo
sorgente ed è possibile fare click in un punto per spostarsi nel corrispondente
codice.

Uno degli editor più utilizzati è TeXworks. Per impostarlo a compilare con
`lualatex` basta scrivere come prima riga del file sorgente questo commento:

```text
% !TeX program = lualatex
```

Queste righe di commento vengono chiamate *righe magiche* e influenzano l'editor
su diversi aspetti uno dei quali è appunto stabilire come verrà compilato il
file al click sul bottone nella barra degli strumenti o alla pressione della
combinazione di tasti `CTRL + T`.

![L'interfaccia di TeXWorks pronto a compilare un sorgente con
LuaLaTeX](images/texworks-in-action.svg)
