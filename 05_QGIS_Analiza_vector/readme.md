# Scenariu

 Găsirea celei mai optime locații pentru o fabrică!
 
 ### Cum ar trebui să arate rezultatul?
 ![locatii_fabrica](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/05_QGIS_Analiza_vector/Data/Workshop/locatii.png)
 
 #### Criterii:
 * Să fie pe teren arabil;
 * Să fie la 500 m de localități (intravilan)
 * Să fie la 5000 m de liniile de înaltă tensiune
 * Să fie la 500 m de drumuri


## Let's jump right in
### Pregătirea datelor
1. Deschideți QGIS
2. Folosind Browser-ul navigați către locația de pe disk unde ați salvat datele.
3. Adaugați în QGIS **tm_clc2018.shp**
> clc este o prescurtare de la Corine Land Cover. Mai multe detalii găsiți [aici](https://land.copernicus.eu/pan-european/corine-land-cover)

4. Deschideți tabelul de atribute pentru stratul **tm_clc2018.shp**. Observați ca informațiile din tabelul de atribute nu ne ajută să identificăm terenurile arabile sau intravilanele, în forma asta. Vom face un **join**! 
5. Din folderul cu date aduceți în QGIS fișierul **clc_descriere.csv** 
6. Deschideți tabelul de atribute și observați că și acest fișier conține câmpul **code_18**. Vom folosi acest camp pentru a face legătura cu fișierul **tm_clc2018.shp** 
7. În panelul de straturi, executați click dreapta pe **tm_clc2018.shp** -> Properties -> Alegeți tab-ul Joins -> Executați click pe plus (Add new join). La join layer alegeți **clc_descriere**, la join field și target field alegeți **code_18**
8. Bifați căsuța din dreptul **Joined Fields** și alegeți/bifați **descriere**
9. Bifați căsuta din dreptul **Custom Field Name Prefix**, și înlocuiți *clc_descriere_* cu **j_**
> în acest fel orice câmp adăugat în urma *join-ului* va avea prefix-ul j
10. Click OK.
11. Click OK pentru a închide fereastra de Layer Properties.
12. Deschideți din nou tabelul de atribute pentru fișierul **tm_clc2018.shp** și observați apariția câmpului nou **j_descriere**
> Join-ul nu este permanent. Este o operațiune activă atâta timp cât proiectul QGIS este deschis. Pentru a face stratul permanentul executați click dreapta -> Export -> Save features as
13. În acest moment, folosindu-ne de câmpul **J_descriere** putem selecta din **tm_clc2018.shp** terenurile arabile
14. Având tabelul de atribute deschis pentru **tm_clc2018.shp** executați click pe **Select by expression**
15. În fereastra nou deschisă scrieți următoarea expresie:
```sql
 "j_descriere" in ( ' Land principally occupied by agriculture with significant areas of natural vegetation' , 'Non irigated arable land' )
```
16. Executați click pe butonul **Select features**
17. Observați că obiectele selectate apar cu culoare albastră în tabelul de atribute și cu galben pe hartă.
18. Acum putem exporta terenul arabil. Click dreapta pe **tm_clc2018.shp** -> Export -> Save Selected Features as
19. La File Name navigați către folderul dvs. de date, creați un subfolder numit Solutie_Workshop și dați un nume fișierului nou, de exemplu *tm_teren_arabil*
20. De asemenea este o ocazie foarte bună să reproiectăm fișierul în sistemul național de proiecție. La CRS alegeți Stereo 70 - EPSG 3844
21. Click ok
22. Observați că layer-ul nou creat apare in QGIS, în panelul de straturi. Pentru moment putem să îl debifăm.
23. Selectatți stratul **tm_clc2018**, deschideți tabelul de atribute, dacă l-ați închis și deselectați obiectele selectate.
24. În continuare vom repeta pașii de mai sus pentru selectarea intravilanelor, folosind de această dată următoarea expresie:
```sql
 "j_descriere" in ( ' Discontinuous urban fabric' , ' Industrial or commercial units' )
```
25. Salvați obiectele selectate în subfolderul Soluție_Workshop cu denumirea **intravilan.shp**
> Nu uitați să reproiectați layer-ul!

### Realizarea analizei

1. Fabrica trebuie să fie la **500 m** față de intravilan. Putem obține acest lucru aplicând un **buffer** fișierului **intravilan.shp**
2. Mergeți în **Processing Toolbox** și scrieți în căsuța de căutare **buffer**
> Dacă nu aveți panoul de Processing Toolbox activ, apăsați pe iconița care seamănă cu o rotiță, din bara de instrumente.
> O altă opțiune este să folosiți bara de căutare din stânga jos!
3. Alegeți prima opțiune executând dublu click.
4. În fereastra nou deschisă, la **Input layer** alegeți **intravilan.shp**, la **Distance** - 500m, bifați opțiunea **Dissolve result** iar la **Buffered**, alegeți **Save to file** și navigați către ...\Soluție_Workshop și denumiți fișierul creat **intravilan_500m**
5. Repetați procesul si pentru liniile de înaltă tensiune și drumuri, adaptând parametrul distanță conform criteriilor.
> Pentru fișierul de drumuri, bifați și opțiunea **Dissolve result**
6. La final, observați că QGIS denumește automat fișierele după numele algoritmului folosit. Puteți să le selectați și sa le eliminați din panoul de straturi. 
7. Mergeți în QGIS Browser, acționați butonul de refresh și navigați către ...\Soluție_Workshop. Observați straturile create. Selectați-le și adaugați-le în QGIS.
8. Ordonați-le în panoul de straturi astfel încăt să fie vizibile toate (de exemplu drumurile să fie peste terenurile arabile).
9. Pentru a satisface criteriile, următorul pas este să realizăm o intersecție între terenurile arabile și buffer-ul liniilor de tensiune. Căutați în **Processing Toolbox** după **Intersection**.
10. La **Input Layer** alegeți **teren_arabil.shp**, iar la **Overlay layer** alegeți **linii_tensiune_buffer500m**. Întrucât rezultatul intersecției este un strat intermediar, nu este necesar să-l salvați pe disk.
11. Acum vom face o diferență între layer-ul nou creat, **Intersection** în panoul de straturi și **intravilan.shp**, întrucât vrem să eliminăm suprafețele acoperite de intravilane. Cautați în **Processing Toolbox** după algoritmul **Difference**. La **Input Layer** alegeți **Intersection**, iar la **Overlay Layer** alegeți **intravilan.shp**. Și layer-ul creat este unul intermediar, prin urmare nu este necesar să îl salvați pe disk. Va apărea în panoul de straturi cu denumirea **Difference**
12. Urmează să intersectăm rezultatul diferenței cu fișierul de drumuri. Căutați în **Processing Toolbox** după **Intersection**, alegeți la **Input Layer** fișierul **Difference**, iar la **Overlay Layer** fișierul **drumuri_buffer500m.shp**. Click pe run!
13. Vom folosi algoritmul **Dissolve**, iar la input Layer vom alege layer-ul **Intersection**
14. În acest moment fișierul nostru este un singur poligon. Pentru a avea poligoane distincte pentru fiecare entitate vom rula algoritmul **Multipart to singlepart** cu mențiunea că acum vom salva pe disk fișierul rezultat deoarece acesta este forma aproape finală!
15. Urmează acum să evaluăm care dintre poligoanele rezultate sunt mai mari de 10.00 ha!
16. Având layer-ul **rezultat_final** selectat în panoul de straturi, deschideți tabelul de atribute, porniți editarea și folosind **Field Calculator** adaugați un câmp nou, numiți-l **suprafata** de tip **decimal number (real)**, la outpit field scrieți 10, iar la precision 2, iar în câmpul de expresii folosiți:
```
$area/10000
```
17. Click OK. Observați în tabelul de atribute câmpul nou creat și valorile pentru suprafață.
18. Cu tabelul de atribute deschis, executați click pe **Select by expression** și folosiți următoarea expresie pentru a selecta doar obiectele cu suprafață mai mare sau egală cu 10.00 ha:
```sql
"suprafata" < 10
```
19. Cu tabelul de atribute deschis și cu editarea pornită ștergeți obiectele selectate
20. Opriți editarea și salvați modificările făcute.

### Felicitări! Ați experimentat cu succes folosirea tehnicilor GIS în găsirea celor mai optime locații pentru o fabrică!
