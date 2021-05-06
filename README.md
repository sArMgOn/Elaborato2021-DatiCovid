# Elaborato2021-DatiCovid

## Bozza inserimento dati ASL

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
| ASL | Azienda Sanitaria Locale, si occupa di inserire i dati nel database a cui accedono tramite credenziali. | username, password | <u>regione, provincia, lat, long, data</u> |
| ANDAMENTO | Padre delle relazioni sottostanti |  | <u></u>
| SANITARIO | Dati relativi a ospedalizzazioni (ingressi, guariti, deceduti) e isolamento domiciliare | ingressi_ospedalizzazioni, ingressi_terapia_intensiva, ingressi_isolemento_domiciliare, dimessi_guariti, dimessi, deceduti | <u>data</u> |
| CASO | Casi di positività, sospetta e non, e guariti | nuovi_positivi, guariti, casi_sospetto_diagnostico, casi_screening | <u>data</u> |
| TAMPONE | Risultati dei tamponi effettuati |tot_molecolare_odierno, tot_antigenico_rapido_odierno, positivi_test_molecolare, positivi_test_antigenico_rapido | <u>data</u> |


### Relazioni
| Nome Relazione | Descrizione | Entità coinvolte | Attributi |
| :------------: | :---------: | :--------------: | :-------: |
| REGISTRAZIONE | Registrazione dei dati pervenuti | ASL e ANDAMENTO | |
