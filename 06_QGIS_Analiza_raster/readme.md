![analiza raster](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/06_QGIS_Analiza_raster/Resurse/Img/qgis_analiza_raster_50px.png)

## Scenariu
**O noua acțiune de împădurire cu *Picea Abies (Molid)* va avea loc în [Parcul Național Retezat](www.retezat.ro), iar sarcina dvs. ca analist GIS este să identificați locațiile optime pentru această acțiune.**

### Criterii
1. Altitudinea trebuie să fie între 1200 - 1600 m;
2. Panta trebuie să fie între 10 și 50 de grade;
3. Orientarea să fie NV, N și NE (0-70 grade și 290-360 grade);
4. Zona nu trebuie să se suprapună cu zonele deja împădurite :)

### Obiective
 * Download SRTM direct în QGIS folosind plugin-ul **SRTM Downloader** care permite descărcarea datelor de la Nasa direct în QGIS
 * Explorarea modalităților de vizualizarea ale rasterelor în QGIS
 * Reproiectare și clip raster pentru zona de interes
 * Analiză raster basic
    * Calcularea pantelor
    * Calcularea orientării versanților
    * Reclasificare raster folosind **Raster Calculator** și algoritmul **Reclassify by Table**
    * Folosirea algoritmului **Rasterize**
    * Folosirea **Raster Calculator** pentru a obține soluția finală
