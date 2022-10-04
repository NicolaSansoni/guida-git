# Git per il singolo

Questa parte si occupa dei seguenti comandi:
- `init`
- `status`
- `add`
- `commit`
- `remote`
- `push`
- `pull`

### Inizializzare un nuovo progetto

Creiamo una cartella che conterrà il nostro progetto. Chiamiamo questa cartella **project**. Entriamo quindi dentro la cartella.

```bash
mkdir project
cd project
```

Inizializziamo **Git**, il nostro _Version Control System_.

```bash
git init
```

Possiamo ora monitorare lo stato del nostro progetto.

```bash
git status
```

Otteniamo la risposta:

> ```
> On branch master
>
> No commits yet
> ```

Il nostro progetto è stato quindi correttamente inizializzato.

## Il primo commit

Creiamo un nuovo file che contiene del testo.

```bash
echo "Questo è il README del mio progetto" > README.md
```

Se ora controlliamo lo stato del nostro progetto vediamo che Git ha visto il nuovo file, ma non lo sta ancora tracciando.

```bash
git status
```

> ```bash
> On branch master
> 
> No commits yet
> 
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
> 	README.md
> ```

Aggiungiamo il nostro nuovo file al progetto.

```bash
git add README.md
git status
```

> ```bash
> On branch master
> 
> No commits yet
> 
> Changes to be committed:
>   (use "git rm --cached <file>..." to unstage)
> 	new file:   README.md
> ```

Per salvare i cambiamenti al nostro progetto dobbiamo eseguire un **commit**.
Puoi pensare ai commit come a dei punti di salvataggio del progetto. Passando da un commit all'altro è possibile esplorare il progetto nelle sue diverse versioni, vedendo quindi come si evolve nel tempo.

```bash
git commit -m "Questo è il mio primo commit"
```

L'opzione _-m_ ti permette di aggiungere un messaggio al commit. È buona norma inserire in questo commit un riassunto di cosa sia cambiato dal commit precedente a questo.   
Nota bene che il messaggio è obbligatorio, e nel caso l'opzione _-m_ sia omessa Git apre per te un editor di testo in cui inserire questo messaggio.

Possiamo visualizzare i commit del progetto con il comando

```bash
git log
```

> ```bash
> Author: nsanso <nsansoni97@gmail.com>
> Date:   Tue Oct 4 12:29:59 2022 +0200
> 
>     Questo è il mio primo commit
> 
> ```

## Tracciare più file

Aggiungiamo adesso un nuovo file, e modifichiamo il README.md già esistente.

```bash
echo '{"message": "Questo è un file JSON"}' > data.json
echo "Questo progetto contiene un README e un file JSON" >> README.md
```

Visualizziamo lo stato del nostro progetto

```bash
git status
```

> ```bash
> On branch master
> Changes not staged for commit:
>   (use "git add <file>..." to update what will be committed)
>   (use "git restore <file>..." to discard changes in working directory)
> 	modified:   README.md
> 
> Untracked files:
>   (use "git add <file>..." to include in what will be committed)
> 	data.json
> ```

Vediamo che Git si è accorto che il file _README.md_, che era stato aggiunto in precedenza, è stato modificato. Si è anche accorto che è stato aggiunto alla cartella un nuovo file, _data.json_.

Aggiungiamo tutte le modifiche nella cartella corrente, quindi sia il nuovo file che i cambiamenti al file già esistente, al progetto:

```bash
git add .
git status
```

> ```bash
> On branch master
> Changes to be committed:
>   (use "git restore --staged <file>..." to unstage)
> 	modified:   README.md
> 	new file:   data.json
> ```

Committiamo le modifiche. Vogliamo inserire un messaggio più lungo, dato che abbiamo aggiunto più modifiche. Omettiamo quindi l'opzione _-m_ e utilizziamo l'editor di testo.

```bash
git commit
```

Scrivi le seguenti righe come messaggio:

```text
Questo è il mio secondo commit

Ho aggiunto un nuovo file ed ho modificato un file già esistente.
Git tiene traccia di entrambi.
```

Salva ed esci dall'editor. Nel caso non abbia aggiunto un messaggio il commit viene annullato. Visualizza i commit del progetto e verifica che sia presente anche il nuovo.

```bash
git log
```

> ```bash
> commit bf6095ce5f0ee53de0eb0a19e170d533ca9dad29 (HEAD -> master)
> Author: nsanso <nsansoni97@gmail.com>
> Date:   Tue Oct 4 12:55:21 2022 +0200
> 
>     Questo è il mio secondo commit
>     
>     Ho aggiunto un nuovo file ed ho modificato un file già esistente.
>     Git tiene traccia di entrambi.
> 
> commit 51c28b525caa53bca8aeca7606813a3ea64d1f17
> Author: nsanso <nsansoni97@gmail.com>
> Date:   Tue Oct 4 12:29:59 2022 +0200
> 
>     Questo è il mio primo commit
> ```

Quando il tuo progetto avrà molti commit potrebbe interessarti vedere un riassunto dei commit presenti. Puoi farlo con il seguente comando:

```bash
git log --oneline
```

> ```bash
> bf6095c (HEAD -> master) Questo è il mio secondo commit
> 51c28b5 Questo è il mio primo commit
> ```









