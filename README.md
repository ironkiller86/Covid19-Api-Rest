# Covid19-Api-Rest

- [Cosa è Covid19-Api e perchè](#description-project)
- [Come funziona](#work)
- [Come si accede ai Dati](#how-to)
<div id="description-project"></div>

## Cosa è Covid19-Api e perché:

**Covid19 Api** come il nome suggerisce è un Api rest che fornisce i dati italiani sul corona virus prelevandoli direttamente dal [repository ufficiale della protezione civile](https://github.com/pcm-dpc/COVID-19).
Il progetto nasce con lo scopo di creare qualcosa di utile per gli altri developer, e allo stesso tempo cercare di mettere in pratica le nozioni apprese sul mondo back-end, creando un qualcosa di concreto, dato che nasco come front-end developer.

Ci tengo a precisare, che l' **API non vuole assolutamente sostituire gli strumenti ufficiali forniti dalla Protezione Civile** sull'andamento dell'epidemico in Italia, e che i dati forniti dal sistema potrebbero non essere più aggiornati,in qualsiasi momento e senza nessun preavviso, qualora il repository ufficiale non dovesse essere più aggiornato da parte dell'ente predisposto.

Se qualcosa non dovesse funzionare oppure avete un consiglio da darmi, potete tranquillamente o aprire un issue, altresì contattarmi direttamente da [Qui](https://www.donatotuzzolino.com/)

<div id="work"></div>

## Come funziona:

Ogni giorno intorno alle 18:00 la protezione civile pubblica sul suo repository ufficiale un file csv contenente i dati sul Covid-19 aggiornati e suddivisi per regione.
Quest'ultimi vengono prelevati e trasformati in un formato _machine readable_, nello specifico il formato **JSON**, e salvati in un database.
Tramite uno specifico **endPoint** è possibile ottenere i dati di tutte le regioni, oppure di una specifica località, o ottenere i dati di un determinato giorno.
Inoltre è possibile poter ordinare questi dati in modo decrescente o crescente specificando alcuni campi chiave.

Per avere accesso ai dati è necessari fornire quando si chiama l 'endPoint un **ApiKey**, altrimenti il dato richiesto non viene fornito.
Per ottenere _l' ApiKey_ ho creato una semplice pagina di _signUp_ che [trovi qui](https://www.donatotuzzolino.com/covidDashboard/) dove si ci puoi registrare attraverso la propria email.
Subito dopo l'utente riceve una prima email contenente un link per confermare la propria identità e successivamente una seconda email la quale questa volta contiene la propria apiKey.
Quest'ultima non ha scadenza, è unica e dovrà sempre essere fornita quando si richiede un dato all Api.

<div id="how-to"></div>

## Come si accede ai dati:
