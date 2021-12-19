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

# Contenuti 📂

- [Rotte](#-rotte-dell-applicazione)
- [Parametri](###-parametri)
- [Eccezioni](#-eccezioni)
- [Testo JUNIT](#-test-junit) 
- [Struttura](#-struttura-del-progetto)
- [Documentazione](#-documentazione)
- [Autori](#-autori-del-progetto)

# Rotte dell'Applicazione :airplane:

>Le richieste che l'utente può effettuare tramite Postman devono essere all'indirizzo [localhost:8080](http://localhost:8080) 

>Facendo attenzione che la porta non sia già occupata dal un'altra applicazione

**Tipo** | **Rotta** | **Descrizione**
--|:--:|--
`GET` | `/userInfo` | Restituisce le informazioni principali dell'utente, poi si può anche inserire il nome di un parametro per ottenre un'informazione in particolare; se non viene inserito niente ritornerà il sesso dell'utente
`GET` | `/filter` | Permette di inserire anno, mese o giorno per visualizzare quali album sono stati inseriti in quel lasso di tempo, facendo quindi statistiche
`GET` | `/filter/name` | Permette di inserire il nome di un album; se è presente nell'account allora verranno stampate a chermo le sue caratteristiche insieme a quelle dell'utente
`GET` | `/filter/volgar-word` | Tramite un file di testo chiamato "VOLGAR_NAME" è possibile inserire una lista di nomi volgari e censurabili; lanciando questa get, se l'utente ha un album con uno di questi nomi verrà segnalato a schermo


### Parametri

Nelle rotte possono essere inseriti dei parametri per avere delle richieste specifiche sull'utente; questi parametri sono quelli ceh possono essere chiamati tramite [Facebook for developers](https://developers.facebook.com). Se viene insierito un parametro diverso o sbagliato, con un tipo non consono al parametro, verrà visualizzato un errore. Questi parametri si possono anche trovare sul file di testo incluso nelle cartelle "GOOD_REQUEST".

## Prima Rotta: /userInfo
La prima rotta restituisce un JSONObject, cioè l'elenco degli attrivuti basici dell'utente. C'è poi la possibilità di inserire un parametro (`param`) per ottnere un'informazione aggiuntiva riguardo l'utente, che di default è la lista degli album tramite un Array. Se viene inserito il nome di un parametro o il valore in modo incorretto verrà segnalato tramite degli errori. Ecco un esempio di chiamata senza il passaggio di nessun parametro e invece poi con il passaggio del parametro `birthday`

>Senza il passaggio del parametro

![Schermata 2021-12-17 alle 23 15 39](https://user-images.githubusercontent.com/92955826/146614167-b6499538-ef23-4d6c-8c94-6477a747d4e2.jpg)
![Schermata 2021-12-17 alle 23 15 56](https://user-images.githubusercontent.com/92955826/146614176-c70eb1b4-b798-4c7a-b075-f340b776841d.jpg)

>Con il passaggio del parametro `birthday`

![Schermata 2021-12-17 alle 23 18 25](https://user-images.githubusercontent.com/92955826/146614393-2a32eb8e-1813-4612-bb94-90a378d53123.jpg)

## Seconda Rotta: /filter
La seconda rotta restituisce un JSONObject contenente l'array degli album trovati per quel lasso di tempo scritto nei filtri come parametro, poi viene visualizato l'Id, il nome, l'e-mail dell'utente e inoltre il conto degli album trovati. Obbligatoriamente deve essere passato almeno un paramentro, cioè `year`, dopo di che a scelta si puo inserire anche il mese(`month`) e poi il giorno(`day`); non si può inserire il giorno senza aver prima scritto il mese e l'anno, perchè senno verrebbe visualizzato a schermo un errore. Se vengono inseriti dei parametri incorretti, alterati o causali veranno visualizzati degli errori. Verrà tenuto conto del numero di giorni di ogni mese per evitare di non trovare nessun album in quel giorno perché non esiste il giorno.

>Con il passaggio del parametro `year`

![Schermata 2021-12-17 alle 23 30 55](https://user-images.githubusercontent.com/92955826/146615522-d7132663-4083-4329-ae67-2441284f2d7e.jpg)
![Schermata 2021-12-17 alle 23 31 15](https://user-images.githubusercontent.com/92955826/146615526-51d6e215-8cbf-44d2-b328-93e965bba076.jpg)

>Con il passaggio dei parametri `year`, `month`, `day`

![Schermata 2021-12-17 alle 23 33 13](https://user-images.githubusercontent.com/92955826/146615609-16c7dadf-d610-4014-a294-f3f700af0595.jpg)

## Terza Rotta: /filter/name

La terza rotta restituisce, se viene trovato l'album di cui abbiamo inserito il nome tramite il parametro `name`, un JSONObject contenente le infomarzio riguardo quell'album e di seguito quelle riguardo l'utente. Nel caso non venga inserito nessun nome o il nome inserito non combaci con nessun album presente nell'account dell'utente, verranno segnalati a schermo degli errori.

>Con il passaggio del parametro `name`

![Schermata 2021-12-18 alle 19 26 30](https://user-images.githubusercontent.com/92955826/146652002-b8081ed3-c880-4b80-8ed2-fd9ec90f72bd.jpg)

## Quarta Rotta: /filter/volgar-word

La quarta rotta restituisce, se viene trovato un album con un nome volgare o censurabile segnalato nel file di testo `VOLGAR_NAME`, un JSONObject con le informazioni di quell'album e dell'utente; inoltre verrà mandato a schermo un link per segnalare la presenza di questo album alla polizia postale italiana. Nel caso non venga trovato nessun album con un nome vietato verrà segnalato a schermo un errore.

>Nel file di testo è stato inserito il vocabolo `cavolo`

![Schermata 2021-12-18 alle 19 33 26](https://user-images.githubusercontent.com/92955826/146652159-c4d18986-cb70-4bf6-afa2-5451bfebcfab.jpg)


# Eccezioni ❌

elenco delle eccezioni personalizzate e non

# Test JUNIT ⚠️

>Ecco di seguito i test che vengono eseguiti su questo programma

![Schermata 2021-12-18 alle 15 29 13](https://user-images.githubusercontent.com/92955826/146645251-0fc15cdf-827c-4e77-8927-761df1f47d37.jpg)
![Schermata 2021-12-18 alle 15 29 18](https://user-images.githubusercontent.com/92955826/146645253-a2a30346-2df8-4cd1-a66b-351ce6265e6e.jpg)
![Schermata 2021-12-18 alle 15 29 47](https://user-images.githubusercontent.com/92955826/146645255-c49c0ca2-56fe-4db8-aeef-032d621d5807.jpg)
![Schermata 2021-12-18 alle 15 30 03](https://user-images.githubusercontent.com/92955826/146645256-b15730c2-f858-4a62-ae75-2f0038808b83.jpg)
![Schermata 2021-12-18 alle 15 30 12](https://user-images.githubusercontent.com/92955826/146645257-e11612d2-fe1c-4859-8775-df357a5df713.jpg)
![Schermata 2021-12-18 alle 15 30 20](https://user-images.githubusercontent.com/92955826/146645258-daf754ab-c0a7-4074-b305-9e28d05a1aca.jpg)
![Schermata 2021-12-18 alle 15 35 13](https://user-images.githubusercontent.com/92955826/146645259-8069ae73-5919-4f16-b9e1-5eb3c2beafab.jpg)

# Struttura del Progetto :office:

screenshot della struttura

# Documentazione 📰
Tutta la documentazione del codice java è integrato al programma tramite Javadoc (trasformare questa parola in un link che apre la cartella Doc del programma)

# Autori del progetto :it: :smile:

Nome | Contributo
-- | :--:
[Baldelli Gianluca](https://github.com/Bxster) | 50%
[Bellante Luca](https://github.com/lucabellantee) | 50%


