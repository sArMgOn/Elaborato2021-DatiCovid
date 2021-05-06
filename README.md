# Elaborato2021-DatiCovid

## Bozza inserimento dati ASL

| regione | provincia | data | #contagi | #tamponi | #tamponi_positivi | #tamponi_negativi | #guariti | #ospedalizzazioni | #decessi | #quarantena |  
| :-----: | :-------: | :--: | :------: | :------: | :---------------: | :---------------: | :------: | :---------------: | :------: | :---------: | :----------------: |

* ASL
    * regione
    * provincia
    * lat
    * long
    * data

* ingressi_ospedalizzazioni
* ingressi_terapia_intensiva
* ingressi_isolamento_domiciliare



## Dizionario dei Dati

### Entità
| Nome Entità | Descrizione | Attributi | Identificatore |
| :---------: | :---------: | :-------: | :------------: |
| ASL | Azienda Sanitaria Locale, si occupa di inserire i dati nel database a cui accedono tramite credenziali. | username, password | *regione, provincia, lat, long, data* |


### Relazioni
| Nome Relazione | Descrizione | Entità coinvolte | Attributi |
| :------------: | :---------: | :--------------: | :-------: |
