# masteringcode.github.io
Mastering Code Web Site

## Descrizione
Questo è il repository del progetto relativo al sito ufficiale di Mastering Code, realizzato con Jekyll e hostato sulla Organization Page di GitHub. Da notare che il deploy è automatizzato sul contenuto della master branch.

## Come modificare il progetto

Anche se piccole modifiche possono essere apportate direttamente con un text editor e controllare direttamente il risultato online, è sempre meglio provare localmente le proprie modifiche su una branch diversa da master tramite installazione locale di Jekyll e poi attraverso la classica PR su master.

## Installazione di Jekyll
La cosa migliore è utilizzare Windows Linux Subsystem di Windows 10, seguendo i passi seguenti:

### Installare WLS (Windows Subsystem for Linux)

Per installare WLS conviene seguire la [guida Microsoft](https://docs.microsoft.com/it-it/windows/wsl/install-win10) e installare Ubunto, seguendo la seguente avvertenza nell'uso di WLS:

- Il disk space di Windows viene reso disponibile in WLS automaticamente tramite un'operazione di mount, quindi è possibile (anzi obbligatorio) utilizzare una cartella di Windows per il progetto che si vuol editare. Non usare MAI lo spazio WLS per registrare i dati se non si vuol incasinare tutto e rischiare di perdere i dati alla chiusura di WLS.

### Installare Jekyll su WLS

Avendo fatto alcune prove, sconsiglio vivamente di utilizzare il terminale WLS di VS Code per eseguire i seguenti passi di installazione, che vanno invece sempre esguiti dal terminale di Ubuntu, disponibile direttamente dal menù start dopo aver installato WLS nel nostro Windows 10.

Come prima cosa, verificare che `apt-get` sia aggiornato. Aprire il terminale di Ubuntu da start ed eseguire:

```
sudo apt-get update
```

Poi occorre installare Ruby, eseguendo nel terminale il seguente comando:

```
sudo apt-get install ruby-full build-essential zlib1g-dev
```

E poiché è meglio evitare di installare le `Ruby Gems` come utente root, occorre impostare una directory per l'installazione delle `Ruby Gems` per il vostro user account, eseguendo i seguenti comandi sempre nel terminale Ubuntu (potete copiare ed eseguire tutto in una volta):

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Ora è possibile installare Jekyll col seguente comando:

```
gem install jekyll bundler
```

e completare il tutto installando il tema di default (che come side effect carica altre `Ruby Gems` necessarie per il funzionamento di Jekyll):


```
gem install minima
```

### Istallare VS Code e l'estensione Shell Launcer

Una volta completata l'installazione di Jekyll, si può passare a Visual Studio Code (se non l'avete ancora installato lo potete scaricare e installare da [questa pagina](https://code.visualstudio.com/download)) e installare l'utilissima estensione che consente di lanciare diversi tipi di terminale da VS Code, in particolare quello che serve a noi per eseguire i comandi di Jekyll, ovvero il terminale WLS.
Si tratta dell'estensione `Shell laucher` che può essere installata sia direttamente dalla sezione delle estensioni di VS Code, che dalla [pagina del marketplace](https://marketplace.visualstudio.com/items?itemName=Tyriar.shell-launcher).

Una volta installato seguendo le istruzioni di configurazione riportate nella pagina dell'estensione, con `CTRL+SHIFT+T` potrete facilmente aprire il terminale WLS direttamente da VS Code, senza quindi aver mai più bisogno di aprire il terminale di Ubuntu.

## Utilizzare Jekyll

Una volta clonato il progetto da GitHub, per visualizzarne il contenuto in locale basta aprire il terminale WLS di VS Code ed eseguire il seguente comando:

```
jekyll serve --livereload
```

A seguito dell'esecuzione di tale comando ill sito viene pubblicato sulla port 4000 di localhost e grazie all'opzione `--livereload` ogni modifica o aggiunta effettuata sulla branch viene automaticamente intercettata e produce in automatico la ricostruzione del sito statico e il refresh della pagina web in corso di visualizzazione.

Per maggiori informazioni su come funziona Jekyll si rimanda alla [documentazione ufficiale](https://jekyllrb.com/docs/).
