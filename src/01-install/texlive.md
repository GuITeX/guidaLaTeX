# Installazione locale di TeX Live

La modalità classica di lavorare con il sistema TeX è quello di installarlo sul
proprio computer. [TeX Live](https://tug.org/texlive/) è una distribuzione TeX
completa, multipiattaforma, scaricabile liberamente dai server
[CTAN](https://ctan.org/).

Esistono alternative, quella più nota è forse [MiKTeX](https://miktex.org/).
Tutto sommato è importante citarle, ed è utile sapere che esistono versioni di
TeX Live per specifici sistemi operativi. Per brevità ci focalizzeremo su TeX
Live *vanilla* con le dovute eccezioni.

La cosa più importante da sapere di TeX Live è che ha un ciclo di sviluppo a
salti: ogni anno viene rilasciata una nuova versione. In quel momento, i
pacchetti della nostra installazione locale non riceveranno più aggiornamenti.

![I rilasci annuali di TeX Live](images/tl-cycle.svg)

Siamo noi a dover decidere se e quando passare alla versione successiva. Di
solito chi utilizza LaTeX in modo continuativo esegue l'upgrade al rilascio
della nuova versione di TeX Live per disporre sempre di una piattaforma
aggiornata e con nuove funzionalità.

Ogni rilascio annuale di TeX Live si installa allo stesso modo e non elimina la
versione precedente che potrà eventualmente essere eliminata successivamente.

> [!NOTE]
> In questa guida verrà consigliata la procedura più semplice, la
> *Net installation* e con lo schema di installazione *completo* di TeX Live.
> Per le altre modalità di installazione o per conoscere gli schemi disponibili
> consulta questa [guida](https://tug.org/texlive/doc.html).

L'installazione completa di TeX Live comprende più di 5000 pacchetti,
comprendente la *documentazione di sistema*, i font con licenza libera e occupa
circa 10 GiB su disco.

Sono qui descritte le procedure passo passo per l'installazione locale di TeX
Live per i principali sistemi operativi desktop, per [Windows](windows.md), per
[macOS](macos.md). Per Linux la guida è doppia [la prima](linux.md) per una
procedura semplice, [la seconda](linux-tlsafe.md) da riga di comando e
totalmente sicura con verifica crittografica.
