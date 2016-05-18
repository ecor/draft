
# Codice R per Analisi dei Dati Raccolti 

Il lavoro consiste nella creazione di un tool R sotto forma di pacchetto R (http://r-project.org) per iniziare l'interpretazione dei dati l'analisi dei dati raccolti. 
Lo scopo di questo task è rendere l'analisi il più possibile riproducibile e legata ai dati originali.
Si sono presi i dati finora raccolti, nei formati CSV,GeoJSON e SHP e sono stati imporatati dentro l'ambiente R come oggetti data frames. 

### Perché un pacchetto R? 

Il pacchetto R è la manniera più concisa per mettere assieme diverse funzioni R e per meglio organizzare un lavoro, o almeno questa è la speranza! Se lo scopo è quindi creare un pacchetto che permetta la riproducibilità del trattamento partendo dai dati originali, uno script R con alcune funzioni raggruppate in un pacchetto , può essere una soluzione.


### Installazione di 'Rcode4healthAsbestos'

Entrando in ambiente R facendo uso del pacchetto "devtools" si =

> library(devtools)
>
> install_github("....")



### Come usare il primo script con 'rcode4health-asbestos'

Si carica il pacchetto:

> library(Rcode4healthAsbestos)
>

si crea la stringa contentente il path dello script R per importare i dati raccolti in formato CSV, GEOJSON ed SHP ed attualmente presenti nella cartella 'dati' del progetto 'code4health' . (Lo script può esere trovato anche nella sottocartella 'r-code4health/inst' , nome del file 'amianto_italia.R') 


>  file <- system.file("amianto_italia.R",package="Rcode4healthAsbestos")

Si lancia lo script

>  source(file)

Lo script legge ogni sinfolo file ed importa i dati organizzati in una lista. ATTUALMENTE gli elementi corrispondenti ai files in formato SHP (shapefile) e GeoJSON sono letti come SpatialPointDataFrame o SpatialPolygonDataFrame mentre  gli elementi letti in files CSV rimangono semplici oggetti di classe data frame. Infine un file csv viene scritto contenenti informazioni sui data frames importati.
Lo script fa usa dell'unica funzione attualmente implementata "getAsbestosFile" la cui documentazione si può ottenere come:

> help(getAsbestosFile,help_type="html")

Questa funzione ATTUALMENTE legge ongi silo files (cioè ogni singola sorgente di dati)  è un wrapper di 'readOGR' (pacchetto "rgdal") per i dati SHP e GEOJSON , già georeferenziati, mentre nel caso CSV usa "read.data" (pachetto base). 
La funzione è in divenire, nel senso che prossimamente inserirò una opzione per georeferenziare direttamente i CSV dai campi coordinate trovati nelle tabelle. 
Ultariori lavori sulle tabelle sono da farsi via via seguendo le indicazioni fornite nei file README.md che si creeranno per ogni sorgente di dato. 
