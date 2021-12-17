# Progetto-Programmazione-Ad-Oggetti 

### Descrizione in italiano :it:

L' applicazione SpringBoot permette, tramite l'API di Facebbok, di avere informazioni circa un utente, come il suo nome, il suo id o la sua e-mail e permette di avere statische riguardo gli album pubblicati dall'utente, vedendoli in base all'anno, al mese o al giorno di pubblicazione. Grazie ad un Client, come ad esempio [Postman](https://www.postman.com), si può accedere alle funzionalità di questa applicazione usando le varie rotte rese disponibili.

### Description of the project :england:

The SpringBoot application allows, through the Facebbok API, to have information about a user, like his name, his id or his e-mail and allows you to have statistics about the albums published by the user, viewing them based on the year, month or day of publication. Thanks to a Client, such as [Postman](https://www.postman.com), you can access the functions of this application using the various routes made available.


## Plus del programma :heavy_plus_sign:

:white_check_mark: Far visualizzare al programma i vari Id e Token tramite un file di testo

# Rotte dell'Applicazione :airplane:

>Le richieste che l'utente può effettuare tramite Postman devono essere all'indirizzo

>[localhost:8080](http://localhost:8080)

**Tipo** | **Rotta** | **Descrizione**
--|:--:|--
`GET` | `/userInfo` | Restituisce le informazioni principali dell'utente, poi si può anche inserire il nome di un parametro per ottenre un'informazione in particolare; se non viene inserito niente ritornerà il sesso dell'utente
`GET` | `/filter` | Permette di inserire anno, mese o giorno per visualizzare quali album sono stati inseriti in quel lasso di tempo, facendo quindi statistiche


### Parametri

Nelle rotte possono essere inseriti dei parametri per avere delle richieste specifiche sull'utente

## Autori del progetto :it: :smile:

**NOME** | **CONTRIBUTO**
-- | --:
[Gianluca Baldelli](https://github.com/Bxster) | 50%
[Luca Bellante](https://github.com/lucabellantee) | 50%



