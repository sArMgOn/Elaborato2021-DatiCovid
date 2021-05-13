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
| Ricovero | Ricovero delle persone in terapia intensiva | Ospedale e Persona | data_ricovero, data_dimissione | 

## Schema Relazionale

#### Entità

Provincia ( <u>codice_provincia</u>, denominazione, regione )
Persona ( <u>codice_fiscale</u>, data_nascita, occupazione, sintomi, stato_salute )
ASL ( <u>codice_azienda</u>, username, password, cap, via, num_civico )
Ospedale ( <u>codice_struttura</u>, nome, cap, via, num_civico )
Tampone ( <u>codice_tampone</u>, tipo, esito )

#### Associazioni

Residenza ( <u>provincia</u>, <u>cf</u> )
V.I.R. provincia con codice_provincia
V.I.R. cf con codice_fiscale
poiche (1,1) => 
> Persona ( <u>codice_fiscale</u>, data_nascita, occupazione, sintomi, stato_salute, <u>provincia</u> )

Quarantena ( <u>cf_p</u>, <u>cod_prov</u>, inizio_quarantena, fine_quarantena )

Ricovero ( <u>code_ospedale</u>, <u>cf_ricoverato</u>, data_ricovero, data_dimissione )
V.I.R. code_ospedale con codice_struttura
V.I.R. cf_ricoverato con codice_fiscale

Test ( <u>tampone</u>, <u>testato</u>, data_prescrizione, data_risultato )
V.I.R. tampone con codice_tampone
V.I.R. testato con codice_fiscale

Prescrizione ( <u>cod_tampone</u>, <u>cod_ASL</u> )
V.I.R. cod_tampone con codice_tampone
V.I.R. cod_ASL con codice_azienda
poiche (1,1) =>
> Tampone ( <u>codice_tampone</u>, tipo, esito, <u>cod_ASL</u> )

Località ( <u>codice_ASL</u>, <u>cod_provincia</u> )
V.I.R. codice_ASL con codice_azienda
V.I.R. cod_provincia con codice_provincia
poiche (1,1) =>
> ASL ( <u>codice_azienda</u>, username, password, cap, via, num_civico, <u>cod_provincia</u> )

Località Ospedaliera( <u>codice_osp</u>, <u>provincia_osp</u> )
V.I.R. codice_osp con codice_struttura
V.I.R. cod_provincia con codice_provincia
poiche (1,1) =>
> Ospedale ( <u>codice_struttura</u>, nome, cap, via, num_civico, <u>provincia_osp</u> )

### Schema Relazionale Completo

Persona ( <u>codice_fiscale</u>, data_nascita, occupazione, sintomi, stato_salute, <u>provincia</u> )
Quarantena ( <u>cf_p</u>, <u>cod_prov</u>, inizio_quarantena, fine_quarantena )
Ricovero ( <u>code_ospedale</u>, <u>cf_ricoverato</u>, data_ricovero, data_dimissione )
Test ( <u>tampone</u>, <u>testato</u>, data_prescrizione, data_risultato )
Tampone ( <u>codice_tampone</u>, tipo, esito, <u>cod_ASL</u> )
ASL ( <u>codice_azienda</u>, username, password, cap, via, num_civico, <u>cod_provincia</u> )
Ospedale ( <u>codice_struttura</u>, nome, cap, via, num_civico, <u>provincia_osp</u> )
Provincia ( <u>codice_provincia</u>, denominazione, regione )