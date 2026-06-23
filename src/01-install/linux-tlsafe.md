# TeX Live sicuro su Linux

I passi qui descritti potrebbero dover essere adattati alla tua distribuzione
Linux. Ci riferiremo a distro Debian e derivate, come Ubuntu. Per distro
differenti mandaci la tua guida all'installazione. Per come fare vai alla
sezione [Contribuire alla guida](../91-misc/contribute.md).

Tutta la procedura prevede solo comandi da terminale, come da tradizione Linux,
e la massima sicurezza di livello crittografico per un'installazione
configurata, pronta all'uso e sicura.

> [!TIP]
> Se non volete digitare i comandi copiateli e incollateli nel terminale con un
> CTRL + Shift + V

## Passo 1: pulizia

Sul tuo sistema potresti avere la TeX Live installata tramite il gestore di
pacchetti della distro. Nessun problema ma qui parliamo di una TeX Live fresca,
installata direttamente da CTAN, al di fuori del sistema dei pacchetti.

Se vuoi eliminarla apri un terminale e esegui i tre comandi:

```bash
sudo apt update && sudo apt upgrade
sudo apt remove --purge texlive*
sudo apt autoremove
```

## Passo 2: firma GPG

Il team di TeX Live firma i file con una chiave crittografica come descritto in
questa [pagina](https://tug.org/texlive/verify.html). Per importare la chiave
pubblica esegui il comando:

```bash
gpg --auto-key-locate=wkd --locate-keys "tex-live@tug.org"
```

L'output del comando è qualcosa di simile a:

```text
gpg: chiave 0D5E5D9106BAB6BC: chiave pubblica "TeX Live Distribution <tex-live@tug.org>" importata
gpg: Numero totale esaminato: 1
gpg:               importate: 1
pub   rsa2048 2016-03-19 [SC]
      C78B82D8C79512F79CC0D7C80D5E5D9106BAB6BC
uid           [ sconosciuto] TeX Live Distribution <tex-live@tug.org>
sub   rsa2048 2016-03-19 [E]
sub   rsa2048 2016-03-19 [S] [scadenza: 2027-07-13]
```

Una volta importata la chiave sarà possibile verificare i file firmati dal Team.

## Passo 3: archivio

Scarichiamo il necessario in una directory temporanea, chiamiamola `temp-tl`,
posizionata nella `home` dell'utente. I file da scaricare sono:

- l'installer ufficiale
- il file con il suo checksum `sha-512`
- e il file di firma del checksum

Ecco i comandi:

```bash
cd ~
mkdir temp-tl
cd temp-tl
wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz.sha512
wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz.sha512.asc
```

## Passo 4: sicurezza

Effettueremo una doppia verifica: prima controlleremo l'autenticità del checksum
per essere certi che nessuno abbia alterato i codici di controllo, poi
verificheremo con esso l'integrità del file compresso `install-tl-unx.tar.gz`.

### Verifica del checksum

```bash
gpg --verify install-tl-unx.tar.gz.sha512.asc install-tl-unx.tar.gz.sha512
```

con l'output:

```text
gpg: Firma effettuata mar 16 giu 2026, 01:49:32 CEST
gpg:                utilizzando la chiave RSA D8F2F86057A857E42A88106A4CE1877E19438C70
gpg: Firma valida da "TeX Live Distribution <tex-live@tug.org>" [sconosciuto]
gpg: ATTENZIONE: questa chiave non è certificata con una firma fidata.
gpg:          Non ci sono indicazioni che la firma appartenga al proprietario.
Impronta digitale chiave primaria: C78B 82D8 C795 12F7 9CC0  D7C8 0D5E 5D91 06BA B6BC
     Impronta digitale della sottochiave: D8F2 F860 57A8 57E4 2A88  106A 4CE1 877E 1943 8C70
```

L'importante è leggere alla terza riga "Firma valida...". Ottimo.

### Verifica dell'archivio

Ora che il checksum è sicuro, verifichiamo con esso l'archivio:

```bash
sha512sum --check install-tl-unx.tar.gz.sha512
```

Il responso è:

```text
install-tl-unx.tar.gz: OK
```

E se l'output mostra OK, il file è integro, sicuro al 100% e pronto per l'uso.
Diversamente elimina il file e ripeti il download da un altro mirror.

## Passo 5: estrazione e installazione

Ora che l'archivio ha superato i controlli di sicurezza, possiamo procedere
all'estrazione e all'installazione vera e propria. L'archivio si estrae con
l'utility `tar` che genera una cartella in cui ci sposteremo:

```bash
tar -xzf install-tl-unx.tar.gz
cd install-tl-20*
```

Volendo installare TeX Live in una cartella di sistema, per l'avvio
dell'installer sono necessari i privilegi di amministratore che assumiamo
tramite il comando `sudo`. Verrà richiesta la password:

```bash
sudo ./install-tl
```

Scegliamo di installare TeX Live nella directory di sistema `/opt/texlive/2026`.
Tutti gli utenti potranno utilizzarla. Nell'interfaccia testuale, alla linea
"Enter command:" premi la lettera D per *directories* e invio per confermare.

Nel sottomenù dai il numero 1 e digita la directory `/opt/texlive/2026` e
conferma al solito con il tasto invio. Poi R per ritornare al menù principale e
I per avviare l'installazione.

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

Add /opt/texlive/2026/texmf-dist/doc/man to MANPATH.
Add /opt/texlive/2026/texmf-dist/doc/info to INFOPATH.
Most importantly, add /opt/texlive/2026/bin/x86_64-linux
to your PATH for current and future sessions.

Logfile: /opt/texlive/2026/install-tl.log
```

## Passo 6: eliminazione temp-tl

Eliminiamo la directory temporanea non più necessaria.

```bash
cd ~
rm -rf temp-tl
```

## Passo 7: configurazione

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
export PATH=/opt/texlive/2026/bin/x86_64-linux:${PATH}
```

Esci salvando e ricarica senza riavviare le impostazioni d'ambiente con il
comando:

```bash
source ~/.profile
```

## Passo 8: Test di funzionamento

Verifichiamo che il sistema riconosca correttamente LaTeX. Digita nel terminale:

```bash
lualatex --version
```

Se compare il testo che inizia con `This is LuaHBTeX, Version 1.24.0...` la
procedura è terminata con successo. Il tuo ambiente TeX Live è installato,
aggiornato e sicuro.

## Passo 9: aggiornare TeX Live

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
alias sutlmgr="sudo /opt/texlive/2026/bin/x86_64-linux/tlmgr"
```

Potrai usare `sutlmgr` per acquisire gli aggiornamenti dei pacchetti. I comandi
più comuni sono:

```bash
# per controllare la presenza di aggiornamenti:
tlmgr update --list

# per aggiornare tutto:
sutlmgr update --all

# per controllare se un pacchetto è installato:
tlmgr show <nome_del_pacchetto>
```
