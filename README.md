# Covid19-Api-Rest

- [Cosa è Covid19-Api e perchè](#description-project)
- [Come funziona](#work)
- [Come si ottengono i dati](#how-to)
<div id="description-project"></div>

## Cosa è Covid19-Api e perché:

**Covid19 Api** come il nome suggerisce è un Api rest che fornisce i dati italiani sul Corona virus prelevandoli direttamente dal [repository ufficiale della Protezione Civile](https://github.com/pcm-dpc/COVID-19).
Il progetto nasce con lo scopo di creare qualcosa di utile per gli altri developer, e allo stesso tempo per cercare di mettere in pratica le nozioni apprese sul mondo back-end, creando un qualcosa di concreto, dato che nasco come front-end developer.

Ci tengo a precisare, che l' **API non vuole assolutamente sostituire gli strumenti ufficiali forniti dalla Protezione Civile** sull'andamento dell'epidemia in Italia, e che i dati forniti dal sistema potrebbero non essere più aggiornati,in qualsiasi momento e senza nessun preavviso, qualora il repository ufficiale non dovesse essere più aggiornato da parte dell'ente predisposto.

Se qualcosa non dovesse funzionare oppure avete un consiglio da darmi, potete o aprire un Issue, altresì contattarmi direttamente da [Qui](https://www.donatotuzzolino.com/)

<div id="work"></div>

## Come funziona:

Ogni giorno intorno alle 18:00 la Protezione Civile pubblica sul suo repository un file csv contenente i dati sul Covid-19 aggiornati e suddivisi per regione.
Quest'ultimi vengono prelevati e trasformati in un formato _machine readable_, nello specifico il formato **JSON**, e salvati in un database.
Tramite uno specifico **endPoint** è possibile ottenere i dati di tutte le regioni, oppure di una specifica località, o ottenere i dati di un determinato giorno.
Inoltre è possibile poter ordinare questi dati in modo decrescente o crescente specificando un campo chiave.

Per avere accesso ai dati è necessario fornire quando si chiama l 'endPoint un **ApiKey**, altrimenti il dato richiesto non viene fornito.
Per ottenere _l' ApiKey_ ho creato una semplice pagina di _signUp_ che [trovi qui](https://www.donatotuzzolino.com/covidDashboard/) dove si ci puoi registrare attraverso la propria email.
Subito dopo l'utente riceve una prima email contenente un link per confermare la propria identità e successivamente una seconda email la quale questa volta contiene la propria apiKey.
Quest'ultima non ha scadenza, è unica e dovrà sempre essere fornita quando si richiede un dato all Api.

<div id="how-to"></div>

## Come si ottengono i dati:

L'endPoint da chiamare per ottenere i dati è il seguente:

> https://covid-19-ita-api.herokuapp.com/covidApi/v1/italy/?apiKey=apiKey

Il dato ritornato è un JSON contenete un array di oggetti, e ogni oggetto rappresenta un Regione.

Es:

```JSON
{
    "data": [
        {
            "data": "2021-05-16T17:00:00",
            "stato": "ITA",
            "codice_regione": 13,
            "denominazione_regione": "Abruzzo",
            "lat": 42,
            "long": 13,
            "ricoverati_con_sintomi": 199,
            "terapia_intensiva": 22,
            "totale_ospedalizzati": 221,
            "isolamento_domiciliare": 6747,
            "totale_positivi": 6968,
            "variazione_totale_positivi": 76,
            "nuovi_positivi": 100,
            "dimessi_guariti": 63820,
            "deceduti": 2454,
            "casi_da_sospetto_diagnostico": "",
            "casi_da_screening": "",
            "totale_casi": 73242,
            "tamponi": 1515023,
            "casi_testati": 644318,
            "note": "",
            "ingressi_terapia_intensiva": 3,
            "note_test": "",
            "note_casi": "",
            "totale_positivi_test_molecolare": 73242,
            "totale_positivi_test_antigenico_rapido": 0,
            "tamponi_test_molecolare": 1072382,
            "tamponi_test_antigenico_rapido": 442641,
            "codice_nuts_1": "ITF",
            "codice_nuts_2": "ITF1"
        },
        {
            "data": "2021-05-16T17:00:00",
            "stato": "ITA",
            "codice_regione": 17,
            "denominazione_regione": "Basilicata",
            "lat": 40,
            "long": 15,
            "ricoverati_con_sintomi": 107,
            "terapia_intensiva": 9,
            "totale_ospedalizzati": 116,
            "isolamento_domiciliare": 5022,
            "totale_positivi": 5138,
            "variazione_totale_positivi": -103,
            "nuovi_positivi": 92,
            "dimessi_guariti": 19925,
            "deceduti": 564,
            "casi_da_sospetto_diagnostico": "",
            "casi_da_screening": "",
            "totale_casi": 25627,
            "tamponi": 358814,
            "casi_testati": 197459,
            "note": "IL NUMERO TOTALE DEI DECESSI COMPRENDE 21 PAZIENTI NON RESIDENTI, DECEDUTI  IN STRUTTURE OSPEDALIERE DELLA REGIONE BASILICATA.",
            "ingressi_terapia_intensiva": 1,
            "note_test": "",
            "note_casi": "",
            "totale_positivi_test_molecolare": 25627,
            "totale_positivi_test_antigenico_rapido": 0,
            "tamponi_test_molecolare": 343608,
            "tamponi_test_antigenico_rapido": 15206,
            "codice_nuts_1": "ITF",
            "codice_nuts_2": "ITF5"
        },
        ...
    ],
    "statusCode": 200,
    "message": "ok",
}
```

<br><br>
E' possibile fare una ricerca per una determinato giorno, aggiungendo il parametro `dataTime`.

Omettendo il campo `dataTime` il dato ritornato sara l'ultimo disponibile in quel dato momento.

> https://covid-19-ita-api.herokuapp.com/covidApi/v1/italy/?dataTime=2021-04-23&apiKey=apiKey

<br><br>
Oppure si può fare una ricerca per una determinata regione in un dato giorno specificando il campo `region`.

Es:

> https://covid-19-ita-api.herokuapp.com/covidApi/v1/italy/?region=Sicilia&dataTime=2021-04-30&apiKey=apiKey

<br><br>
Inoltre è possibile fare una ricerca per un determinato campo ordinado i risultati in ordine crescente (che il default) o decrescente.<br>
I parametri da aggiungere in querystring sono `orderBy` e `sortBy`.

Es:

> https://covid-19-ita-api.herokuapp.com/covidApi/v1/italy/?sortBy=desc&orderBy=nuovi_positivi&dataTime=2021-04-30&apiKey=apiKey
