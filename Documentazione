# Documentazione file JSON per Finencial

Questo file JSON definisce la struttura delle lezioni di Finencial. Il file JSON viene trasformato in codice HTML da un programma.

## Struttura file

Il file è un array, ogni elemento rappresenta una lezione

``` json
[
    {
        "IDlezione": 1,
        "titolo": "Lezione 1",
        "livello": 0,
        "tempo": 10,
        "imgLezione": "../../img/lezione1/intro.png",
        "testo": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. <sb>Subtitole</sb> Donec volutpat nisi ac eros lacinia placerat. Donec elementum sapien vitae semper ornare. Quisque ut nunc eu neque rhoncus mollis.<img1>",
        "file":[
            {
                "id": "img1",
                "tipo": "immagine",
                "src": "../../img/lezione1/img1.png",
                "descrizione": "descrizione dell'immagine"
            },

            ...
        ],

        "quiz": [
            {
                "id":"q1",
                "tipo":"multipla",
                "domanda":"Testo della domanda",
                "risposte":["Risposta1", "Risposta2", "Risposta3","Risposta4"],
                "risCorretta": 0
            },

            ...
        ]
    }
]
```

## IDlezione
``` json
    "IDlezione": 1,
```
- **Tipo:** number
- **Obbligatorio:** si
- **Vincoli:** numero intero >=1, deve essere univoco per ogni elemento
- **Descrizione:** identifica in modo univoco la lezione

## Titolo
``` json
    "titolo": "Introduzione a Finencial",
```

- **Tipo:** string
- **Obbligatorio:** si
- **Vincoli:** non possono esistere due lezioni con lo stesso titolo
- **Descrizione:** nome della lezione, viene mostrato all'utente e come titolo della scheda HTML

## Livello
``` json
    "livello": 0,
```

- **Tipo:** number
- **Obbligatorio:** si
- **Vincoli:** numero intero >=0
- **Descrizione:** Determina la difficoltà del contenuto e può essere utilizzato per filtrare o ordinare le lezioni nell’interfaccia. 

|Numero|Livello|
|---|---|
|0|Base|
|1|Avanzato|

Valori aggiuntivi potranno essere introdotti in versioni future.

## Tempo
``` json
    "tempo": 10,
```

- **Tipo:** number
- **Obbligatorio:** si
- **Vincoli:** numero intero >=0
- **Descrizione:** Indica il tempo stimato per completare la lezione, l'unità di misura è il minuto.

## Immagine lezione
``` json
    "imgLezione": "../../img/lezione1/intro.png",
```

- **Tipo:** string
- **Obbligatorio:** si
- **Vincoli:**
    - deve essere un percorso relativo valido
    - la cartella deve seguire la convenzione: lezione`<IDlezione>`
    - il file deve chiamarsi sempre `intro.png`
    - il file deve esistere nel percorso indicato
- **Descrizione:** percorso dell'immagine principale della lezione. <br>
L'immagine viene visualizzato subito dopo il titolo e viene utilizzata anche come immagine della card della lezione nell'interfaccia

#### Convenzione del percorso
**Formato generale:**
``` bash
../../img/lezione<IDlezione>/intro.png
```

**Esempi:**
- Lezione 1: `"../../img/lezione1/intro.png"`
- Lezione 5: `"../../img/lezione5/intro.png"`

> Se il percorso non rispetta la convenzione oppure il file non esiste, l'interfaccia potrebbe non visualizzare alcuna immagine o mostrare un placeholder

## Testo
``` json
    "testo": "Lorem ipsum",
```

- **Tipo:** string
- **Obbligatorio:** si
- **Vincoli:**
    - deve essere una stringa di testo UTF-8
    - può contenere tag speciali (vedere tabella)
    - i riferimenti `<img(id)>` devono corrispondere a un `id` presente nella sezione `file` della stessa lezione 
- **Descrizione:** contiene il contenuto testuale della lezione, che verrà trasformato in HTML dall'applicazione.
    - Il testo viene mostrato nella pagina della lezione
    - i tag speciali permettono di aggiungere formattazioni o elementi multimediali

#### Tag speciali supportati
|Tag|Descrizione|Esempio|
|---|---|---|
|`<sb></sb>`| Indica il sottotitolo di un blocco di testo|`Lorem ipsum <sb>Sottotitolo</sb> dolor sit amet`
|`<img(id)>`| Inserisce l'immagine corrispondente all'`id` definito nella sezione file| `<img1> inserisce l’immagine con "id": "img1"`

## File
``` json
    "file": [
        {
            "id": "img1",
            "tipo": "immagine",
            "src": "../../img/lezione1/img1.png",
            "descrizione": "descrizione dell'immagine"
        }
    ]
```
- **Tipo:** array di oggetti
- **Obbligatorio:** no (ma consigliato)
- **Descrizione:** contiene le risorse multimediali della lezione. Ogni oggetto rappresenta un singolo file e può

#### Proprietà degli oggetti `file`
|Campo|Tipo|Obbligatorio|Vincoli|Descrizione|
|---|---|---|---|---|
|id| string| si| unico all'interno della lezione| Identificativo del file, utilizzato nei tag `<img(id)>`|
|tipo|string|si| attualmente solo `"immagine"`, altri tipi di file potrebbero essere aggiunti in futuro| indica il tipo di file multimediale|
|src| string| si| percorso relativo valido, segue la convenzione `../../img/lezione<IDlezione>/<id>.png`; il file deve esistere| Percorso del file multimediale|
|descrizione| string| si| testuale| Descrizione del file, utilizzata come `alt` nell’HTML

#### Nota sulla convezione dei percorsi

**Formato generale**
``` bash
../../img/lezione<IDlezione>/<id>.png
```

**Esempio**
- Lezione 1, `id=img1` = `../../img/lezione1/img1.png`
- Lezione 1, `id=img3` = `../../img/lezione1/img3.png`
- Lezione 2, `id=img1` = `../../img/lezione2/img1.png`
- Lezione 2, `id=img2` = `../../img/lezione2/img2.png`

>Gli `id` del file devono essere unici solo all'interno della lezione. Se il file non esiste nel percorso indicato, l'immagine non sarà visualizzata

## Quiz
``` json
    "quiz": [
        {
            "id": "q1",
            "tipo": "multipla",
            "domanda": "Testo della domanda",
            "risposte": ["Risposta1", "Risposta2", "Risposta3","Risposta4"],
            "risCorretta": 0
        }
    ]
```

- **Tipo:** array di oggetti
- **Obbligatorio:** si (Almeno 2 elementi)
- **Descrizione:** contiene i quiz associati alla lezione. Ogni oggetto rappresenta una singola domanda.

|Campo|Tipo|Obbligatorio|Vincoli|Descrizione|
|---|---|---|---|---|
|id|string|si|unico all'interno della lezione| identificativo del quiz|
|tipo|string|si| `"multipla"` o `"vero/falso"` |tipo di quiz|
|domanda|string |si| testo UTF-8|testo della domanda|
|risposte|array di string|si| -1 sola risposta corretta per domanda -per quiz a risposta multipla sempre 4 possibilità|risposte possibili|
|risCorretta|number|si| indice della risposta corretta, parte da 0.| indica quale risposta è corretta|

#### Note

- L'indice `risCorretta`si riferisce alla posizione nell'array `risposte`, contando da 0.
- Per il tipo `"vero/falso"`, `risposte` conterrà sempre due elementi: `"Vero"` e `"Falso"`
- Gli id quiz devono essere unici solo all'interno della lezione
