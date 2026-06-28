# Compilare il sorgente

I programmi TeX sono a riga di comando. Compilare un sorgente significa eseguire
il compositore in un terminale passandogli il nome del file.

![Schema di input/output: la compilazione del sorgente](images/compile-latex.svg)

Il file sorgente non viene mai modificato dal compositore. L'effetto della
compilazione è quello di creare il file del documento composto in PDF, e altri
file secondari o ausiliari.

Il comando di compilazione va dato in un terminale scrivendo di seguito:

1. il nome del compositore, generalmente `lualatex`
2. uno spazio di separazione
3. il nome del file con o senza estensione
4. il tasto invio per eseguirlo

```bash
lualatex primodocumento.tex
```

## Estensione e codifica

L'estensione dei file sorgenti è `.tex` e la loro codifica Unicode `UTF-8`. In
questo modo il sorgente viene compilato allo stesso modo su diversi sistemi
operativi. Possiamo editare e compilare lo stesso sorgente in ufficio con
Windows, a casa con Linux e da un amico con macOS.

## Compilare con TeXworks

Gli editor di testo dedicati a LaTeX hanno molte facilitazioni tra cui la
compilazione con un click. Di più, spesso il PDF è mostrato a fianco del testo
sorgente ed è possibile fare click in un punto per spostarsi nel corrispondente
codice.

Uno degli editor più utilizzati è TeXworks. Per impostarlo a compilare con
`lualatex` basta scrivere come prima riga del file sorgente questo commento:

```latex
% !TeX program = lualatex
```

Queste righe di commento vengono chiamate *righe magiche* e influenzano l'editor
su diversi aspetti uno dei quali è appunto stabilire quale deve essere il
compilatore al click sul bottone nella barra degli strumenti o alla pressione
della combinazione di tasti `CTRL + T`.

![L'interfaccia di TeXWorks pronto a compilare un sorgente con
LuaLaTeX](images/texworks-in-action.svg)
