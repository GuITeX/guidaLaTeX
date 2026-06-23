# TeX Live su Linux

I passi qui descritti potrebbero dover essere adattati alla tua distribuzione
Linux perché riferiti alle distro Debian e derivate, come Ubuntu.

Per distro differenti mandaci la tua guida all'installazione. Per come fare vai
alla sezione [Contribuire alla guida](../91-misc/contrubute.md).

> [!TIP]
> Se non volete digitare i comandi copiateli e incollateli nel terminale con un
> CTRL + Shift + V

## Passo 1: archivio

Scarica l'archivio contenente il necessario da questo [link
CTAN](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz) e
procedi con un click destro sulla sua icona a scompattarlo (voce "Estrai" o
simile).

## Passo 2: avvio

Apri la cartella `install-tl-20*` appena creata e con un click destro sullo
sfondo libero da icone scegli "Apri Terminale qui". Nella finestra del terminale
digita il comando seguente e fai invio per eseguirlo:

```bash
sudo ./install-tl
```

Nell'interfaccia testuale, alla linea "Enter command:" premi la lettera I per
*installation* e invio per confermare. Non è necessario modificare paramentri.

I singoli pacchetti saranno scaricati con la protezione del protocollo di rete,
dai server ufficiali CTAN. L'operazione può richiedere da 30 minuti a un'ora o
più, in base alla tua connessione e alla velocità del computer. Vengono poi
generati i file di formato e di ricerca file.

Al termine apparirà il testo di benvenuto:

```text
Benvenuto in TeX Live!
See /opt/texlive/2026/index.html for links to documentation.

The TeX Live web site (https://tug.org/texlive/) provides all updates
and corrections. TeX Live is a joint project of the TeX user groups
around the world; please consider supporting it by joining the group
best for you. The list of groups is available on the web
at https://tug.org/usergroups.html.

...
```

## Passo 3: temp file

Seleziona sia l'archivio compresso che la directory temporanea non più
necessaria e premi `Canc` per eliminarle.

## Passo 4: configurazione

A questo punto TeX Live deve essere configurata manualmente non potendo contare
sugli automatismi del sistema di pacchetti proprio della distribuzione Linux.

Istruiamo Debian/Ubuntu su dove trovare i programmi di TeX Live appena
installati.

Apri il file `.profile` nel tuo editor di testo preferito. Si tratta di un file
*nascosto* della `home` dell'utente. Premendo `CTRL + H` si attiva/disattiva la
visualizzazione delle rispettive icone.

Vai in fondo al file e incolla le seguenti righe:

```bash
# addition for TeX Live 2026
export PATH=/usr/local/texlive/2026/bin/x86_64-linux:${PATH}
```

Esci salvando e ricarica senza riavviare le impostazioni d'ambiente con il
comando:

```bash
source ~/.profile
```

## Passo 5: Test di funzionamento

Verifichiamo che il sistema riconosca correttamente LaTeX. Digita nel terminale:

```bash
lualatex --version
```

Se compare il testo che inizia con `This is LuaHBTeX, Version 1.24.0...` la
procedura è terminata con successo. Il tuo ambiente TeX Live è installato,
aggiornato e sicuro.

## Passo 6: aggiornare TeX Live

L'utility di aggiornamento `tlmgr` ha necessità dei privilegi di amministratore
dovendo scrivere in una directory di sistema. Se lanciamo il comando con `sudo`
l'utility non verrà trovata perché non saranno riconosciti i percorsi
nell'ambiente di esecuzione amministrativo. La soluzione più semplice
consisterebbe nel digitare *tutto* il percorso ma non è comodo.

Basta creare un *alias* all'interno del file `.bash_aliases`. Si tratta di un
nome che prende il posto di un comando lungo utilizzato spesso.

Apri il file `.bash_aliases` nella `home` dell'utente. Se non esiste crealo, e
aggiungi le righe seguenti per creare l'alias `sutlmgr`:

```bash
# addition for TeX Live 2026
alias sutlmgr="sudo /usr/local/texlive/2026/bin/x86_64-linux/tlmgr"
```

Potrai usare `sutlmgr` da terminale per acquisire gli aggiornamenti dei
pacchetti. I comandi più comuni sono:

```bash
# per controllare la presenza di aggiornamenti:
tlmgr update --list

# per aggiornare tutto:
sutlmgr update --all

# per controllare se un pacchetto è installato:
tlmgr show <nome_del_pacchetto>
```
