# Covid19-Api-Rest

- [Cosa è Covid19-Api e perchè](#description-project)
- [Come funziona](#work)
<div id="description-project"></div>

## Cosa è Covid19-Api e perché:

**Covid19 Api** come il nome suggerisce è un Api rest che fornisce i dati italiani sul corona virus prelevandoli direttamente dal [repository ufficiale della protezione civile](https://github.com/pcm-dpc/COVID-19). S
Il progetto nasce con lo scopo di creare qualcosa di utile per gli altri developer, e allo stesso tempo cercare di mettere in pratica le nozioni apprese sul mondo back-end, creando un qualcosa di concreto, dato che nasco come front-end developer.

<div id="work"></div>

## Come funziona:

Ogni giorno intorno alle 18:00 la protezione civile pubblica sul suo repository ufficiale un file csv contenente i dati sul Covid-19 aggiornati e suddivisi per regione.
Quest'ultimi vengono prelevati e trasformati in un formato _machine readable_, nello specifico il formato **JSON**, e salvati in un database.
Tramite uno specifico **endPoint** è possibile ottenere i dati di tutte le regioni, oppure di una specifica località, o ottenere i dati di un determinato giorno.
Inoltre è possibile poter ordinare questi dati in modo decrescente o crescente specificando alcuni campi chiave.

Per avere accesso ai dati è necessari fornire quando si chiama l 'endPoint un **ApiKey**, altrimenti il dato richiesto non viene fornito.
Per ottenere _l' ApiKey_ ho creato una semplice pagina di signUp che [trovi qui](https://www.donatotuzzolino.com/covidDashboard/) dove si ci puoi registrare attraverso la propria email.
Subito dopo l'utente riceve una prima email contenete un link per confermare la propria identità e successivamente una seconda email la quale questa volta contiene la propria apiKey.
Quest'ultima non ha scadenza, è unica e dovrà sempre essere fornita quando si richiede un dato all Api.
