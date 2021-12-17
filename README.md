# Progetto-Programmazione-Ad-Oggetti 

### Descrizione in italiano :it:

L' applicazione SpringBoot permette, tramite l'API di Facebbok, di avere informazioni circa un utente, come il suo nome, il suo id o la sua e-mail e permette di avere statische riguardo gli album pubblicati dall'utente, vedendoli in base all'anno, al mese o al giorno di pubblicazione. Grazie ad un Client, come ad esempio [Postman](https://www.postman.com), si può accedere alle funzionalità di questa applicazione usando le varie rotte rese disponibili.

### Description of the project :england:

The SpringBoot application allows, through the Facebbok API, to have information about a user, like his name, his id or his e-mail and allows you to have statistics about the albums published by the user, viewing them based on the year, month or day of publication. Thanks to a Client, such as [Postman](https://www.postman.com), you can access the functions of this application using the various routes made available.


## Plus del programma :heavy_plus_sign:

:white_check_mark: Far visualizzare al programma i vari Id e Token tramite un file di testo

# Rotte dell'Applicazione :airplane:

>Le richieste che l'utente può effettuare tramite Postman devono essere all'indirizzo [localhost:8080](http://localhost:8080) 

>Facendo attenzione che la porta non sia già occupata dal un'altra applicazione

**Tipo** | **Rotta** | **Descrizione**
--|:--:|--
`GET` | `/userInfo` | Restituisce le informazioni principali dell'utente, poi si può anche inserire il nome di un parametro per ottenre un'informazione in particolare; se non viene inserito niente ritornerà il sesso dell'utente
`GET` | `/filter` | Permette di inserire anno, mese o giorno per visualizzare quali album sono stati inseriti in quel lasso di tempo, facendo quindi statistiche


### Parametri

Nelle rotte possono essere inseriti dei parametri per avere delle richieste specifiche sull'utente; questi parametri sono quelli ceh possono essere chiamati tramite [Facebook for developers](https://developers.facebook.com). Se viene insierito un parametro diverso o sbagliato, con un tipo non consono al parametro, verrà visualizzato un errore.

## Prima Rotta: /userInfo
La prima rotta restituisce un JSONObject, cioè l'elenco degli attrivuti basici dell'utente. C'è poi la possibilità di inserire un parametro (`param`) per ottnere un'informazione aggiuntiva riguardo l'utente, che di default è la lista degli album tramite un Array. Se viene inserito il nome di un parametro o il valore in modo incorretto verrà segnalato tramite degli errori. Ecco un esempio di chiamata senza il passaggio di nessun parametro e invece poi con il passaggio del parametro `birthday`

>Senza il passaggio del parametro

![Schermata 2021-12-17 alle 23 15 39](https://user-images.githubusercontent.com/92955826/146614167-b6499538-ef23-4d6c-8c94-6477a747d4e2.jpg)
![Schermata 2021-12-17 alle 23 15 56](https://user-images.githubusercontent.com/92955826/146614176-c70eb1b4-b798-4c7a-b075-f340b776841d.jpg)

>Con il passaggio del parametro `birthday`

![Schermata 2021-12-17 alle 23 18 25](https://user-images.githubusercontent.com/92955826/146614393-2a32eb8e-1813-4612-bb94-90a378d53123.jpg)

## Seconda Rotta: /filter
La seconda rotta restituisce un JSONObject contenente l'array degli album trovati per quel lasso di tempo scritto nei filtri come parametro, poi viene visualizato l'Id, il nome, l'e-mail dell'utente e inoltre il conto degli album trovati. Obbligatoriamente deve essere passato almeno un paramentro, cioè `year`, dopo di che a scelta si puo inserire anche il mese(`month`) e poi il giorno(`day`); non si può inserire il giorno senza aver prima scritto il mese e l'anno, perchè senno verrebbe visualizzato a schermo un errore. Se vengono inseriti dei parametri incorretti, alterati o causali veranno visualizzati degli errori.

>Con il passaggio del parametro `year`

![Schermata 2021-12-17 alle 23 30 55](https://user-images.githubusercontent.com/92955826/146615522-d7132663-4083-4329-ae67-2441284f2d7e.jpg)
![Schermata 2021-12-17 alle 23 31 15](https://user-images.githubusercontent.com/92955826/146615526-51d6e215-8cbf-44d2-b328-93e965bba076.jpg)

>Con il passaggio dei parametri `year`, `month`, `day`

![Schermata 2021-12-17 alle 23 33 13](https://user-images.githubusercontent.com/92955826/146615609-16c7dadf-d610-4014-a294-f3f700af0595.jpg)

# Autori del progetto :it: :smile:

Nome | Contributo
-- | :--:
[Baldelli Gianluca](https://github.com/Bxster) | 50%
[Bellante Luca](https://github.com/lucabellantee) | 50%
