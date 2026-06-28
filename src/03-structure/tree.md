# Organizzazione di un progetto

Per i documenti complessi è utile suddividere il documento in più file sorgenti
per migliorarne la gestione.

I vantaggi sono:

- file più piccoli facilitano l'editing dei contenuti,
- modificare l'ordine dei capitoli si riduce a spostare singoli comandi,
- la nostra visione sulla struttura del documento migliora,
- i tempi di compilazione possono ridursi sensibilmente.

Con gli editor di testo moderni gli svantaggi sono invero ridotti al minimo. Si
possono tenere aperti molti file allo stesso tempo o fare ricerche su tutti i
file di una directory. I *plug-in* possono gestire nomi e riferimenti presenti
in altri file.

## Inclusione di file

Ogni documento ha un unico sorgente principale detto `main file` all'interno del
quale vengono inclusi altri file tramite il comando `\input{}` o `\include{}`.

Quando il compositore compila il `main file` processerà i file esterni inclusi
in un dato punto come se fossero stati digitati in quella posizione.

Questo ha una conseguenza importante perché quando si scrive un file secondario
i riferimenti come i percorsi a file di immagini, devono essere riferiti alla
directory dove si trova il file principale.

La cartella dove risiede il file principale è detta `root` del progetto. I file
dei singoli capitoli possono appartenere a sotto directory così da tenere
ordinati i vari livelli formando la struttura logica dei contenuti del
documento.

## Il comando `\input{}`

Questo comando è una macro di TeX e non del nucleo di LaTeX. Come unico
argomento accetta il percorso del file da inserire.

Nel percorso i nomi dei file possono essere separati dal carattere di `/`
(slash) indipendentemente dal sistema operativo, partendo dalla cartella di
`root` e l'estensione `.tex` può essere omessa.

Qui un esempio di main file per una ipotetica biografia di un poeta (i sei file
dei capitoli si trovano in una sotto cartella `chapter`):

```latex
% main file
\documentclass{book}

\begin{document}

\input{chapter/00-introduzione}
\input{chapter/01-infanzia}
\input{chapter/02-primo-amore}
\input{chapter/03-il-capolavoro}
\input{chapter/04-anni-guerra}
\input{chapter/99-conclusioni}

\end{document}
```

> [!NOTE]
> Dare buoni nomi ai file e alle cartelle è un'utile arte. Evita di usare
> caratteri spazio o accentati. Se iniziano con una numerazione saranno mostrati
> in ordine voluto e non da quello alfabetico dei nomi.

## Il comando `\include{}`

In LaTeX esiste anche il comando `\include{}` pensato per compilare documenti
complessi suddivisi in capitoli. Con questo comando è possibile compilare in
modo selettivo i capitoli così da limitare il tempo di compilazione.

Lo scenario è quindi quello di un documento complesso, come una tesi per
esempio, che richiede compilazioni frequenti ogni volta che si desidera
controllare il risultato. A mano a mano che si inserisce contenuto i tempi si
allungano.

Dunque è utile compilare solamente una selezione di capitoli, magari anche uno
solo. Nel preambolo `\includeonly{file}` imposta `\include{}` ad inserire solo i
file specificati mantenendo corretti i riferimenti incrociati. Ecco un esempio
di codice:

```latex
% main file
\documentclass{book}

\includeonly{chapter/02-primo-amore,chapter/03-il-capolavoro} 

\begin{document}

\include{chapter/00-introduzione}
\include{chapter/01-infanzia}

% unici due capitoli effettivamente inseriti
\include{chapter/02-primo-amore}
\include{chapter/03-il-capolavoro}

\include{chapter/04-anni-guerra}
\include{chapter/99-conclusioni}

\end{document}
```

A differenza di `\input{}` e a conferma che `\include{}` è pensato per includere
file di capitolo, quest'ultimo inserisce prima e dopo il file anche
un'interruzione di pagina, non può essere usato nel preambolo e non può essere
nidificato, ovvero chiamato all'interno di file secondari.

Per esigenze particolari si può sempre ideare nuovi comandi personalizzati o
utilizzare creativamente quelli esistenti.
