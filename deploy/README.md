# Deploy!

> **Nota** Il seguente capitolo è abbastanza difficile da capire fino in fondo. Non mollare e cerca di portarlo a termine; deployment (termine abbastanza complicato da tradurre, ma indica tutto ciò che tu rendi LIVE, accessibile sul web e non più solo dal tuo computer) è una parte importante nel processo di costruzione di un sito web. Questo capitolo è inserito a metà del tutorial per far sì che il tuo tutor possa aiutarti con il processo leggermente più complesso di messa online del sito. Questo significa che puoi ancora finire il tutorial da sola se sei a corto di tempo.

Fino ad ora il tuo sito è accessibile solo dal tuo computer, ma ora imparerai come metterlo online! Deploying è il processo di pubblicazione online del tuo progetto in modo tale che sia visibile anche da altre persone :).

Come hai già visto, un sito internet ha sede in un server. Ci sono tantissimi server providers disponibili su internet. Noi ne useremo uno che ha un processo di deployment relativamente semplice: [Heroku][1]. Questo provider è gratuito per piccole applicazioni che non hanno troppi visitatori. Sarà quindi perfetto per te al momento.

 [1]: https://heroku.com/


# Git

Git è un "sistema di controllo versione" utilizzato da un sacco di programmatori. Questo software può tracciare le modifiche nel corso del tempo ad i file, in questo modo puoi ripristinare successivamente una specifica versione. Un pò come l'opzione "traccia modifiche" in Microsoft Word, ma molto più potente.

### Heroku CLI
> **Nota** Se hai già fatto la procedura di installazione, non devi farlo di nuovo - si può passare alla sezione successiva e iniziare a creare il tuo repository.

#### Windows
È possibile scaricare Heroku cli dal sito ufficiale: https://devcenter.heroku.com/articles/heroku-cli#download-and-install.
#### MacOS
È possibile scaricare Heroku cli dal sito ufficiale: https://devcenter.heroku.com/articles/heroku-cli#download-and-install.


## Inizializzare un repository Git

Git tiene traccia delle modifiche a un particolare insieme di file in quello che è chiamato repository di codice (o "repo" in breve). Iniziamone uno per il nostro progetto. Apri la console ed esegui questi comandi nella directory `ahsubsdesign`:

> **Nota** controlla la directory su cui stai lavorando adesso con il comando `pwd`(OSX/Linux) oppure `cd`(Windows) prima di iniziare il repository. Dovresti essere nella cartella `ahsubsdesign`.

    $ git init
    Initialized empty Git repository in ~/ahsubsdesign/.git/
    $ git config --global user.name "Your Name"
    $ git config --global user.email you@example.com
    

Dobbiamo inizializzare il repository git solo una volta per ogni progetto (e non dovrai più reinserire il nome utente e l'email).

È una buona idea usare il comando `git status` prima di `git add` oppure ogni volta che non sei sicuro di cosa sia cambiato. Questo aiuterà ad evitare eventuali brutte sorprese, come file sbagliati che vengono aggiunti o a cui viene fatto il commit. Il comando `git status` restituisce informazioni riguardanti qualsiasi file non tracciato/modificato/in staging, lo stato del branch e molto altro. L'output dovrebbe essere simile a:

    $ git status
    On branch master
    
    Initial commit
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    
            .gitignore
            blog/
            manage.py
            mysite/
    
    nothing added to commit but untracked files present (use "git add" to track)
    

E finalmente salviamo le nostre modifiche. vai alla tua console ed esegui questi comandi:

    $ git add --all .
    $ git commit -m "La mia app Django, primo commit"
     [...]
     111 files changed, 244 insertions(+)
     create mode 100644 .gitignore
     create mode 100644 Procfile
     create mode 100644 README.md
     create mode 100644 manage.py

     [...]
     create mode 100644 mysite/wsgi.py
     create mode 100644 runtime.txt
    

## Pubblichiamo il nostro codice su Heroku

Vai su [Heroku.com][1] e registrati per ottenere un nuovo account gratuito. (Se l'hai già fatto nella preparazione, è fantastico!)

Quindi,apriamo il terminale o prompt dei comandi e iniziamo a scrivere:` heroku login` Così facendo stiamo dicendo a heroku cli di fare il login con le nostre credenziali in modo da poter finalmente creare la nostra prima webapp django; una volta fatto, possiamo andare a creare la nostra applicazione con il comando: heroku create nomeapp (dove nomeapp è il nome scelto per la nostra app su heroku)
.


> **Nota** Il nome `nomeapp` è importante -- potresti scegliere qualcos'altro, ma si ripeterà un sacco di volte nelle istruzioni qui sotto, e dovrai sostituirlo ogni volta. Probabilmente è più facile mantenere il nome `nomeapp`.

Nella schermata successiva, ti verrà mostrato l'URL per clonare il tuo repo:


Ora abbiamo bisogno di collegare il repository Git sul tuo computer a quello su Heroku.

Digita quanto segue sulla tua console:

        $ git push heroku master
    

Dovresti vedere qualcosa di simile:

    Counting objects: 14, done.
    Delta compression using up to 4 threads.
    Compressing objects: 100% (9/9), done.
    Writing objects: 100% (14/14), 3.97 KiB | 0 bytes/s, done.
    Total 14 (delta 0), reused 0 (delta 0)
    remote: Compressing source files... done.
    remote: Building source:
    remote: -----> Python app detected
    remote: -----> Installing python-3.6.2
    remote: -----> Installing pip
    remote: -----> Installing requirements with pip
    [...]
    remote:   https://nomeapp.herokuapp.com/ deployed to Heroku
    

<!--TODO: maybe do ssh keys installs in install party, and point ppl who dont have it to an extention -->

# Sei live!

La pagina predefinita per il tuo sito dovrebbe dire "Welcome to Django", esattamente come sul tuo Pc locale. Prova ad aggiungere `/admin/` alla fine della URL, e verrai portata al sito di amministrazione. Accedi con il tuo username e password, e vedrai che puoi aggiungere nuovi Post sul server.

Dà a te stessa un' *ENORME* pacca sulla schiena! Il deploy dei server è tra le parti più complicate dello sviluppo web e di solito le persone ci impiegano svariati giorni prima di farli funzionare. Ma hai pubblicato il tuo sito su Internet senza sforzo!
