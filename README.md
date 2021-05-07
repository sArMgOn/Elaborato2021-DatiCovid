# Elaborato2021-DatiCovid

## Dati di interesse

* ASL
    * regione
    * provincia
    * lat
    * long
    * data

* ANDAMENTO
    * SANITARIO
        * ingressi_ospedalizzazioni
        * ingressi_terapia_intensiva
        * ingressi_isolamento_domiciliare
        * dimessi_guariti
        * dimessi
        * deceduti
    * CASO
        * nuovi_positivi
        * guariti
        * casi_sospetto_diagnostico
        * casi_screening
    * TAMPONE
        * tot_molecolare_odierno
        * tot_antigenico_odierno
        * positivi_test_molecolare
        * positivi_test_antigenico_rapido

## Dizionario dei Dati

### Entità
| Nome Entità | Descrizione | Attributi | Identificatore |
| :---------: | :---------: | :-------: | :------------: |
| Struttura Sanitaria | Struttura dove si gestiscono tamponi e ospedalizzazioni | CAP, via, num_civico | <u>codice_struttura</u> |
| ASL | Azienda Sanitaria Locale, prescrive tamponi e invia dati a enti superiori | username, password e ereditati da Struttura Sanitaria | <u></u> |
| Ospedale | Gestione ospedalizzazioni e terapie intensive | ereditati da Struttura Sanitaria | <u></u>
| Provincia | Dove risiedono le persone e le Strutture Sanitarie | sigla, regione | <u>codice_provincia</u> |
| Persona | Persona fisica soggetta a COVID-19 | data_nascita, stato_salute, sintomi | <u>codice_fiscale</u> |
| Studente | Persona che frequenta la scuola | ereditati da Persona | |
| Lavoratore | Persona che effettua una qualsiasi attività lavorativa regolamentare | ereditati da Persona | |
| Tampone | Test per la rilevazione del COVID-19 per le persone | tipo, esito | <u>codice_tampone</u> |


### Relazioni
| Nome Relazione | Descrizione | Entità coinvolte | Attributi |
| :------------: | :---------: | :--------------: | :-------: |
| Test | Tampone effettuato da una persona | Tampone e Persona | data_prescrizione, data_risultato |
| Prescrizione | Struttura Sanitaria che prescrive un tampone | Tampone e Struttura Sanitaria | |
| Località | Provincia della Struttura Sanitaria | Provincia e Struttura Sanitaria | |
| Residenza | Provincia di residenza di una Persona | Provincia e Persona | inizio_isolamento, fine_isolamento | 
| Ospedalizzazione | Ricovero delle persone in terapia intensiva | Ospedale e Persona | data_ricovero, data_dimissione | 
