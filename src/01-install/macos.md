# MacOS

Per gli utenti Mac esiste una versione di TeX Live specifica denominata
[MacTeX](https://tug.org/mactex/) adattamento al sistema di installazione per
questo sistema operativo. La versione minima richiesta è la 11 Big Sur.

Gli eseguibili girano nativamente sia su piattaforma Intel sia su quella Apple
Silicon con i processori della serie M.

## Passo 1: scarica MacTeX.pkg

Con un click alla [pagina
ufficiale](https://tug.org/mactex/mactex-download.html) di download oppure
direttamente da qui scarica il pacchetto
[MacTeX.pkg](https://mirror.ctan.org/systems/mac/mactex/MacTeX.pkg) di circa
6.4 GiB di peso.

## Passo 2 (opzionale): sicurezza

Nella pagina di download sono disponibili le stringhe di verifica del file
scaricato, sia per il checksum `md5` sia per `sha512`, il primo è più veloce ma
è il secondo a essere molto più sicuro.

### MD5

Apri il Terminale di macOS (premi Cmd + Spazio e digitando "Terminale").

Digita il comando `md5` seguito da uno spazio, poi trascina e rilascia il file
scaricato all'interno della finestra del terminale (questo inserirà
automaticamente il percorso corretto del file). Il comando sarà simile a questo:
```
md5 ~/Downloads/MacTeX.pkg
```
Premi invio per ottenere la stringa di checksum che dovrebbe essere identica a
quella [qui](https://tug.org/mactex/mactex-download.html) riportata. Se non lo è
il file è corrotto e deve essere scaricato di nuovo.

### SHA-512

Con `sha512` i passi sono simili ai precedenti ma le intenzioni sono differenti:
non solo si vuole accertare che il file scaricato sia quello corretto salvandoci
da errori di rete ma sopratutto controllare se il pacchetto sia sicuro al 100%.

Su macOS, l'algoritmo SHA-512 viene gestito in modo nativo tramite il comando
`shasum` con l'opzione `-a 512` che specifica di utilizzare la variante a 512
bit. Come prima apri il Terminale di macOS. Il comando finale sarà simile a
questo:
```
shasum -a 512 ~/Downloads/MacTeX.pkg
```
Confronta la stringa `sha-512` con questa comando con quella presente
[qui](https://tug.org/mactex/mactex-download.html).

## Passo 3: installazione

Fai click sopra al file scaricato. L'installer apre un dialogo di benvenuto, la
pagina con le informazioni generali e la licenza d'uso, e la pagina finale in
cui compare il bottone "Install". Conviene lasciare l'installazione completa.

## Passo 4: test

Apri un Terminale e digita il comando
```
lualatex --version
```
Se leggi le informazioni di versione tutto è pronto per lavorare con LaTeX sul
tuo Mac.

## Passo 5: aggiornamenti

MacTeX installa anche l'applicazione TeX Live Utility in `Applications/TeX/`.
Essa è l'interfaccia grafica per operare sulla TeX Live e aggiornarla
periodicamente.

## Altre utilità

In MacTeX ci sono anche due editor: TeXShop e TeXworks, entrambe molto comodi
per lavorare con i file sorgenti di LaTeX perché offrono le righe magiche e la
ricerca diretta e inversa tra codice e PDF composto.

E come non menzionare il programma BibDesk che gestisce database
bibliografici.
