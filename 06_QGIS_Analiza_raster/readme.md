![analiza raster](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/06_QGIS_Analiza_raster/Resurse/Img/qgis_analiza_raster_50px.png)

## Scenariu
**O noua acțiune de împădurire cu *Picea Abies (Molid)* va avea loc în [Parcul Național Retezat](www.retezat.ro), iar sarcina dvs. ca analist GIS este să identificați locațiile optime pentru această acțiune.**

### Criterii
1. Altitudinea trebuie să fie între 1200 - 1600 m;
2. Panta trebuie să fie între 10 și 50 de grade;
3. Orientarea să fie NV, N și NE (0-70 grade și 290-360 grade);
4. Zona nu trebuie să se suprapună cu zonele deja împădurite :)

### Obiective
 * Download SRTM direct în QGIS folosind plugin-ul **SRTM Downloader**
 > SRTM este o prescurtare de la **Shuttle Radar Topography Mission**. Puteți citi mai multe detalii [aici](https://en.wikipedia.org/wiki/Shuttle_Radar_Topography_Mission)
 * Explorarea modalităților de vizualizarea ale rasterelor în QGIS
 * Reproiectare și decupare raster pentru zona de interes
 * Analiză raster la nivel de începător
    * Calcularea pantelor
    * Calcularea orientării versanților
    * Reclasificare raster folosind **Raster Calculator** și algoritmul **Reclassify by Table**
    * Folosirea algoritmului **Rasterize**
    * Folosirea **Raster Calculator** pentru a obține soluția finală
    
 ### Pregătirea datelor
 #### Download SRTM
 1. Să instalăm plugin-ul **SRTM Downloader** 
      1. Plugins -> Manage and install plugins -> Selectați tab-ul *All* și scrieți în căsuța de căutare `srtm`
      > Dacă rezultatul căutării este gol, mergeți în tab-ul *Settings* și bifați **Show also experimental plugins** și **Show also deprecated plugins**. De asemenea este necesar să fiți conectat la internet! Repetați căutarea.
      2. Selectați din lista **SRTM Downloader** și executați click pe **Install plugin**
      3. Plugin-ul este instalat și poate fi accesat din meniul Plugins -> SRTM Downloader sau folosind iconița dedicată din bara de instrumente.
 2. Folosind QGIS Browser navigați către calea unde ați salvat datele și aduceți în QGIS fișierul **limita_retezat.shp**
 3. Deschideți plugin-ul SRTM Downloader
 4. Apăsați pe butonul **Set canvas extent**
 5. La **Output-Path** alegeți unde să salvați rasterele, de exemplu ...\Analiza_Raster\Srtm_Downloader
 6. Asigurați-vă că sunteți conectat la internet
 7. Click pe butonul **Download**
 8. În fereastra de Login executați click pe [link](https://urs.earthdata.nasa.gov//users/new) și creați un cont folosind o adresă de e-mail validă.
 9. Verificați adresa de e-mail și confirmați creare contului
 10. Întoarceți-vă în QGIS și introduceți în căsuța de username - user-ul creat și în căsuța de password - parola aleasă.
 11. Opțional bifați **Save Credentials** pentru a nu fi nevoiți să le introduceți de fiecare dată când vreți să downloadați fișierele SRTM folosind acest plugin
 12. Click OK
 13. Observați că pentru zona de interes sunt disponibile 2 imagini raster: **N45023** și **N45022**
 14. După download fișierele sunt automat adăugate în QGIS și simbolizate, în mod implicit cu o paletă de culori alb-negru
 
 #### Normalizarea imginilor raster
Având în vedere ca peste zona noastră de interes se suprapun 2 imagini raster, le vom uni.
1. În bara de meniu principală alegeți Raster -> Miscellaneous -> Build Virtual Raster
2. În fereastra deschisă alegeți la **Input Layers**, executând click pe butonul ... cele două imagini raster descărcate
3. La Resolution lăsați **average**
4. Debifați opțiunea **Place each input file into a separate band**
5. La Resampling alegeși **Bilinear**
6. Puteți salva raster-ul ca și fișier temporar
7. Click pe Run.
8. Rasterul virtual apare în panelul de straturi cu denumirea **Virtual**
9. Asigurați-vă că în acest moment aveți încărcate în QGIS, în panoul de straturi, doar rasterul **Virtual** și fișierul **limita_retezat.shp**. Dacă aveți straturi în plus le puteți elimina pentru a păstra un mediu de lucru ordonat.
10. Ordonați cele doua straturi astfel încât **limita_retezat.shp** să fie deasupra rasterul **Virtual**
11. Observați că rasterul acoperă o zonă mult mai mare așadar este necesar să-l decupăm după zona noastră de interes.
12. În **Processing Toolbox** căutați algoritmul **Clip Raster by Mask Layer**
13. La **Input layer** alegeți rasterul **Virtual**, la **Mask layer** ar trebui să fie deja completat în mod implicit **limita_retezat**
14. Este OK să salvați fișierul decupa ca și fișier temporar
15. Click Run
16. Rasterul decupat apare în panelul de straturi cu denumirea **Clipped (mask)**
17. Debifați sau eliminați din panelul de straturi rasterul **Virtual** și aranjați straturile astfel încât **limita_retezat** să fie peste **Clipped (mask)**
18. În panelul de straturi selectați **limita_retezat**, executați click dreapta -> Properties -> Symvbology -> Simple Fill. **Fill style** selectați **No Brush**, iar la **Stroke color** alegeți o altă culoare, de exemplu roșu.
19. Observați suprapunerea dintre rasterul decupat și limita Parcului Național Retezat
20. Să salvăm și să reproiectăm rasterul **Clipped (mask)**. Selectați-l în panelul de straturi, click dreapta -> Export -> Save as. La format lăsăți **GeoTIFF**, la File name alegeți un nume, de exemplu *srtm_retezat* și o locație unde să îl salvați pe disk. La CRS alegeți EPSG:3844.
21. Click OK.
 
  ### Realizarea analizei
 

 
 
    
