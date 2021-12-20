# Progetto-Programmazione-Ad-Oggetti 

### Descrizione in italiano :it:

L' applicazione SpringBoot permette, tramite l'API di Facebbok, di avere informazioni circa un utente, come il suo nome, il suo id o la sua e-mail e permette di avere statische riguardo gli album pubblicati dall'utente, vedendoli in base all'anno, al mese o al giorno di pubblicazione, oppure cercandoli in base al nome. Grazie ad un Client, come ad esempio [Postman](https://www.postman.com), si può accedere alle funzionalità di questa applicazione usando le varie rotte rese disponibili.
Per far partire l'applicazione bisogna inserire il proprio Id e il proprio Access Token nel file di testo `WRITE_ME` nelle prime due righe; questi parametri si possono visualizzare attraverso il sito [Facebook for Developers](https://developers.facebook.com).

### Description of the project :england:

The SpringBoot application allows, through the Facebbok API, to have information about a user, such as his name, his id or his e-mail and allows you to have statistics about the albums published by the user, seeing them based on per year, month, or day of publication, or by searching for them by name. Thanks to a Client, such as [Postman] (https://www.postman.com), you can access the functions of this application using the various routes made available.
To start the application you need to insert your Id and Access Token in the text file `WRITE_ME` in the first two lines; these parameters can be viewed on the [Facebook for Developers] site (https://developers.facebook.com).

### Plus del programma :heavy_plus_sign:

:white_check_mark: Far visualizzare al programma i vari Id e Token tramite un file di testo

:white_check_mark: Cercare gli album con il loro nome

:white_check_mark: Cercare gli album tramite una lista di parole vietate

:white_check_mark: Se la porta 8080 è occupata, verrà cambiata automaticamente dal programma

# Contenuti 📂

- [Configurazione](#configurazione-key)
- [Rotte](#rotte-dellapplicazione-airplane)
- [Parametri](#parametri)
- [Eccezioni](#eccezioni-)
- [Testo JUNIT](#test-junit-%EF%B8%8F) 
- [Struttura](#struttura-del-progetto-office)
- [Documentazione](#documentazione-)
- [Autori](#autori-del-progetto-it-smile)

# Confiurazione :key:

Tramite il terminale del vostro pc potete clonare questa repository usando questo comando:

git clone -inserire indirizzo repository- 

Dopo di che si puo lanciare il progetto come SpringBoot application trmite un IDE, come [Eclipse](https://www.eclipse.org), oppure dal terminale e quando il programma sarà in esecuzione sarà possibile utilizzarlo tramite un client, come [Postman](https://www.postman.com), contattando l'indirizzo http://localhost:8080

# Rotte dell'Applicazione :airplane:

>Le richieste che l'utente può effettuare tramite Postman devono essere all'indirizzo [localhost:8080](http://localhost:8080) a salire perché il nostro programma ha la funzionalità di cambiare la porta automaticamente se occupata.

| **N°** | **Tipo** | **Rotta** | **Descrizione** |
|--|--|:--:|--|
| [1](#prima-rotta-userinfo) | `GET` | `/userInfo` | Restituisce le informazioni principali dell'utente inserendo inoltre un parametro per ottenre un'informazione in particolare; i parametri accettati si possono trovare sul file di testo "GOOD_REQUEST.txt" |
| [2](#seconda-rotta-filter) | `GET` | `/filter` | Permette di inserire anno, mese o giorno per visualizzare quali album sono stati inseriti in quel lasso di tempo, facendo quindi statistiche |
| [3](#terza-rotta-filtername) | `GET` | `/filter/name` | Permette di inserire il nome di un album; se è presente nell'account allora verranno stampate a schermo le sue caratteristiche insieme a quelle dell'utente |
| [4](#quarta-rotta-filtervolgar-word) | `GET` | `/filter/volgar-word` | Tramite un file di testo chiamato "VOLGAR_NAME.txt" è possibile inserire una lista di nomi volgari e censurabili; lanciando questa get, se l'utente ha un album con uno di questi nomi verrà segnalato a schermo |


### Parametri

Nelle rotte possono essere inseriti dei parametri per avere delle richieste specifiche sull'utente; questi parametri sono quelli che possono essere chiamati tramite [Facebook for developers](https://developers.facebook.com). Se viene insierito un parametro diverso o sbagliato, verrà visualizzato un errore. Questi parametri si possono trovare sul file di testo incluso nelle cartelle "GOOD_REQUEST.txt".

## Prima Rotta: /userInfo
La prima rotta restituisce un JSONObject, cioè l'elenco degli attributi dell'utente. Si deve inoltre inserire un parametro (`param`) per ottnere un'informazione aggiuntiva riguardo l'utente. Se viene inserito il nome di un parametro o il valore in modo incorretto verrà segnalato tramite degli errori. I parametri accettati sono quelli che si trovano all'interno del file di testo "GOOD_REQUEST.txt". Ecco un esempio di chiamata con il passaggio del parametro `birthday`

foto

## Seconda Rotta: /filter
La seconda rotta restituisce un JSONObject contenente l'array degli album trovati per quel lasso di tempo scritto nei filtri come parametro, poi viene visualizato l'Id, il nome, l'e-mail dell'utente e inoltre il conto degli album trovati. Obbligatoriamente deve essere passato almeno un paramentro, cioè `year`, dopo di che a scelta si può inserire anche il mese(`month`) e poi il giorno(`day`); non si può inserire il giorno senza aver prima scritto il mese e l'anno, perchè, nel caso, verrebbe visualizzato a schermo un errore. Se vengono inseriti dei parametri incorretti, alterati o causali veranno visualizzati degli errori. Verrà tenuto conto del numero di giorni di ogni mese per evitare di non trovare nessun album in quel giorno perché non esiste il giorno.

>Con il passaggio del parametro `year`

![Schermata 2021-12-17 alle 23 30 55](https://user-images.githubusercontent.com/92955826/146615522-d7132663-4083-4329-ae67-2441284f2d7e.jpg)
![Schermata 2021-12-17 alle 23 31 15](https://user-images.githubusercontent.com/92955826/146615526-51d6e215-8cbf-44d2-b328-93e965bba076.jpg)

>Con il passaggio dei parametri `year`, `month`, `day`

![Schermata 2021-12-17 alle 23 33 13](https://user-images.githubusercontent.com/92955826/146615609-16c7dadf-d610-4014-a294-f3f700af0595.jpg)

## Terza Rotta: /filter/name

La terza rotta restituisce, se viene trovato l'album di cui abbiamo inserito il nome tramite il parametro `name`, un JSONObject contenente le infomarzioni riguardo quell'album e di seguito quelle riguardo l'utente. Nel caso non venga inserito nessun nome o il nome inserito non combaci con nessun album presente nell'account dell'utente, verranno segnalati a schermo degli errori.

>Con il passaggio del parametro `name`

![Schermata 2021-12-18 alle 19 26 30](https://user-images.githubusercontent.com/92955826/146652002-b8081ed3-c880-4b80-8ed2-fd9ec90f72bd.jpg)

## Quarta Rotta: /filter/volgar-word

La quarta rotta restituisce, se viene trovato un album con un nome volgare o censurabile segnalato nel file di testo `VOLGAR_NAME`, un JSONObject con le informazioni di quell'album e dell'utente; inoltre verrà mandato a schermo un link per segnalare la presenza di questo album alla polizia postale italiana. Nel caso non venga trovato nessun album con un nome vietato verrà segnalato a schermo un errore.

>Nel file di testo è stato inserito il vocabolo `cavolo`

![Schermata 2021-12-18 alle 19 33 26](https://user-images.githubusercontent.com/92955826/146652159-c4d18986-cb70-4bf6-afa2-5451bfebcfab.jpg)


# Eccezioni ❌

Oltre alle eccezioni standard di Java sono state gestite le seguenti eccezioni personalizzate:

# Test JUNIT ⚠️

>Ecco di seguito i test che vengono eseguiti su questo programma

![Schermata 2021-12-20 alle 11 14 02](https://user-images.githubusercontent.com/92955826/146751830-ef7c02dd-de81-41be-b98e-06cf225f18bf.jpg)
![Schermata 2021-12-20 alle 11 14 10](https://user-images.githubusercontent.com/92955826/146751832-65819bd8-ff71-46b5-8234-f1bf5c208211.jpg)
![Schermata 2021-12-20 alle 11 14 20](https://user-images.githubusercontent.com/92955826/146751837-ddd73248-49e9-4d05-a5b9-de9710a60d31.jpg)
![Schermata 2021-12-20 alle 11 14 43](https://user-images.githubusercontent.com/92955826/146751838-53fce4bb-ecaa-4256-badc-e0a7d117384d.jpg)
![Schermata 2021-12-20 alle 11 15 12](https://user-images.githubusercontent.com/92955826/146751840-87342830-19da-48b8-aa22-fb91843a4225.jpg)
![Schermata 2021-12-20 alle 11 15 19](https://user-images.githubusercontent.com/92955826/146751843-f8202a41-6070-4130-ad67-0dc338024f62.jpg)
![Schermata 2021-12-20 alle 11 15 34](https://user-images.githubusercontent.com/92955826/146751845-3d81da76-9952-4909-88f6-8927f9184877.jpg)
![Schermata 2021-12-20 alle 11 16 10](https://user-images.githubusercontent.com/92955826/146751849-a58cb5d8-95c3-46d2-83d1-9e47449ea7d6.jpg)
![Schermata 2021-12-20 alle 11 13 44](https://user-images.githubusercontent.com/92955826/146751827-a4879ed7-3820-4101-bf24-45ee7e04c063.jpg)
![Schermata 2021-12-20 alle 11 16 28](https://user-images.githubusercontent.com/92955826/146751851-420b0b6c-382a-4002-9077-692ccd087f26.jpg)

# Struttura del Progetto :office:

screenshot della struttura

# Documentazione 📰
Tutta la documentazione del codice java è integrato al programma tramite Javadoc (trasformare questa parola in un link che apre la cartella Doc del programma)

# Autori del progetto :it: :smile:

Nome | Contributo
-- | :--:
[Baldelli Gianluca](https://github.com/Bxster) | 50%
[Bellante Luca](https://github.com/lucabellantee) | 50%



