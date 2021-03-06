![QGIS_creare_de_date](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/03_QGIS_Creare_de_date/Resurse/Img/qgis_creare_de_date_github_logo.png)

## Obiective
* Georeferențierea unei imagini sursă;
* Consumarea unui serviciu Web Map Service (WMS);
* Crearea de date vector: *punct, linie, poligon*
* Explorarea datelor vector.

## Let's jump right in

### Data
1. Creați un folder nou într-o locație pe disk, numit `QGIS_Creare_date`;
2. Download data și salvați în folder-ul nou creat.

### QGIS at work
#### Georeferențierea unui set de date raster

> **Georeferențierea** este procesul prin care unei imagini (hartă, imagine satelitară) i se atribuie coordonate, astfel încât orice program GIS să poată poziționa corect imaginea.
> Se poate face fie prin introducerea manuală a coordonatelor, dacă acestea se cunosc, fie prin folosirea unor puncte comune între un fișier deja georeferențiat și fișierul ce urmează să fie georeferențiat.

1. Deschideți QGIS 3.4 și în bara de menu mergeți la Settings -> Options;
2. Selectați tab-ul *CRS*, bifați opțiunea *Use a default CRS* și selectați **EPSG:3844**;
> Citiți mai multe detalii despre [EPSG](http://www.epsg.org/)
3. În bara de menu mergeți la Plugins -> Manage and Install Plugins;
4. Executați click pe tab-ul *Installed* și activați plugin-ul **Georeferencer GDAL**;
5. Executați click pe *Close* pentru a închide fereastra *Plugins | Installed*;
6. În bara de menu mergeți la Raster -> Georeferencer;
7. În fereastra *Georeferencer*, executați click pe *Open raster* și navigați către ...`\QGIS_Creare_date\Date\Raster\Input\variante_centura_tm.jpg`
> Examinați imaginea, încercați să gasiți elemente care să vă ajute la georeferențiere.
8. Minimizați fereastra *Georeferencer* și mergeți înapoi în fereastra principală QGIS;
9. Executați click pe *Open Data Manager*, asigurați-vă că tab-ul *Vector* este selectat și navigați către ...`\QGIS_Creare_date\Date\Vector\subset_ancpi_uat.shp`;
> Pentru a deschide *Open Data Manager* puteți folosi și combinația de taste **CTRL+L**;
10. În acest moment aveți deschise in QGIS, un subset al limitelor de unități administrativ teritoriale (UAT) corespunzator zonei înconjurătoare a municipiului Timișoara;
11. Executați click dreapta pe layer -> Properties și selectați tab-ul *Labels*;
> Puteți activa panoul *Layer Styling* prin apăsarea tastei **F7**
12. Schimbați din *No labels* în *Single labels*;
13. În casuța *Label with* alegeți coloana *name* pentru a eticheta limitele UAT după denumirea lor;
14. Vom georeferenția imaginea cu ajutorul limitelor de UAT;
15. Maximizația fereastra *Georeferencer* și observați că butonul *Add Point* este deja activat;
16. Pe imaginea ce urmează a fi georeferențiată, limitele de UAT sunt simbolizate cu linie punctată de culoare maro;
17. Executați zoom către colțul din stânga al imaginii, la limita dintre Săcălaz și Timișoara și adăugați un punct unde limita își schimbă direcția;
18. În fereastra *Enter Map Coordinates*, executați click pe butonul *From map canvas*;
19. Faceți zoom spre punctul comun și executați click.
> Pentru a fi siguri ca punctul dvs. este pe vertexul dorit puteți activa *snapping*.
> * View -> Toolbars -> Activați Snapping Toolbar;
> * În *Snapping Toolbar*, executați click pe *Enable Snapping*;
> * Executați click pe cel de-al doilea buton și alegeți opțiunea *Advanced Snapping Configuration*, apoi *Open Snapping Options*;
> * Din lista de layere, bifați **subset_ancpi_uat**, la *type* alegeți *vertex*, iar pentru *toleranță* introduceți valoarea **10**;
20. În fereastra *Enter Map Coordinates*, observați că sunt trecute valorile coordonatelor. Apăsați OK.
21. Observați că punctul nou adăugat este marcat cu roșu pe imaginea ce urmează să fie georeferențiață și că apare și în tabelul *GCP table*;
22. Repetați procesul și încercați să mai adaugați cel puțin 3 puncte, situate în colțurile imaginii.
> După adăugarea a cel puțin 4 puncte, în tablul *GCP table*, în rubrica *Residual(pixels)* sunt trecute erorile de georeferențiere. Încercați să adăugați puncte astfel încât să minimizați valorile erorilor.
23. La final, în fereastra de *Georeferencer* executați click pe *Transformation Settings*;
24. La *Transformation type* alegeți **Polynomial 1**, pentru *Resampling method* alegeți **Nearest neighbour**;
> Puteți citi mai multe informații despre tipurile de transformări [aici](https://docs.qgis.org/testing/en/docs/user_manual/plugins/plugins_georeferencer.html#available-transformation-algorithms)
25. Pentru *Target SRS*, alegeți **EPSG:3844**
> Dacă nu îl găsiți în listă, executați click pe butonul *Select CRS*, scrieți la filter *3844* și selectați din listă.
26. Selectați o locație pe disk pentru noul fișier creat;
27. Bifați opțiunea *Load in QGIS when done*;
28. Click OK;
29. Dacă totul a mers bine, ar trebui să aveți în QGIS, în *Layers Panel*, imaginea nou georeferențiată, suprapusă peste limitele de UAT.
30. Acum putem începe să digitizăm *varianta 1 de ocolire Timișoara Sud*, de exemplu.

#### Digitizarea unui obiect de tip **linie**
##### Crearea unui obiect de tip linie

1. În bara de menu mergeți la Layer -> Create Layer -> New Shapefile Layer;
2. În fereastra nou deschisă, la *File name* alegeți un nume pentru fișier și calea unde doriți să il salvați;
> De exemplu `exemplu_linie` salvat la adresa: ...`\QGIS_Creare_date\Date\Vector\Outpur\exemplu_linie.shp`;
3. La *Geometry type* selectați *Line*;
4. Pentru sistemul de coordonate alegeți *EPSG:3844*;
5. Dacă doriți să adaugați atribute, puteți completa rubrica *Name* cu numele câmpului, la *Type* să alegeți tipul acestuia (text, integer ...) și în final să executați click pe *Add to Fields List*;
6. Click OK.
7. Observați că layer-ul nou creat apare in *Layer Panels*.

> Pașii de mai sus sunt identici pentru crearea obiectelor de tip punct, linie sau poligon. Singura diferență fiind la *pasul 3* unde se alege **tipul geometriei**!

##### Digitizarea unui obiect de tip linie
1. Selectați layer-ul în *Layers Panel*;
2. Click pe *Toggle Editing*;
3. Click pe *Add Line Feature*;
4. Alegeți un nivel de zoom corespunzător;
> de exemplu 1: 10 000
4. Începeți să digitizați trasând centrul variantei de ocolire nr. 1!
> examinați legenda hărții și observați cum este simbolizată varianta de ocololire nr. 1.
5. În momentul în care ați terminat de digitizat executați click dreapta.
6. În fereastra care se deschide puteți introduce informațiile referitoare la atribute.
> de exemplu în câmpul *Varianta*, puteți introduce valoarea *1*.


## Adăugarea unei basemap  
QGIS vă permite să adaugați o suită mare de basemap-uri în 2 moduri:
1. Folosind plugin-ul **Quick Map Services**
   1. Pentru instalare alegeți Plugins - Manage and install plugins - în căsuța de căutare scrieți *quick*
   2. Selectați din rezultatele returnate plugin-ul
   3. Executați click pe **Install**
   4. Plugin-ul se regăsește în tab-ul **Web** din bara de meniu principal
   5. Observați că *by default* plugin-ul oferă un număr limita de basemap-uri.
![qms](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/03_QGIS_Creare_de_date/Resurse/Img/qgis_qms.png)
   6. Pentru a avea acces la toate basemap-uri: Web - Quick Map Services - Settings - More Services - Get Contributed Pack - Save
   7. Verificați din nou lista de basemap-uri disponibile!
 
2. Prin folosirea de **XYZ Tiles** din Browser
Pentru a accesa basemap-uri via XYZ Tiles este necesar sa creați o conexiune nouă către link-ul sau URL unde este găzduit serviciul (basemap-ul),să alegeți un nume și să setați un nivel minim și maxim de zoom.

![xyz](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/03_QGIS_Creare_de_date/Resurse/Img/xyz_conn.png)

Din fericire există și o variantă mai simplă, chiar dacă aparent pare mai complicată deoarece implică rularea unui script în Python. Scriptul a fost scris de Klas Karlsson și poate fi descărcat de [aici](https://raw.githubusercontent.com/klakar/QGIS_resources/master/collections/Geosupportsystem/python/qgis_basemaps.py)
   Pentru avea acces la basemap-uri este necesar să efectuați pașii următori:
   1. În interiorul QGIS deschideți consola de Python (fie prin apasarea iconiței din toolbar, fie prin folosirea combinației de taste CTRL+ALT+P);
   2. Din consola de Python executați click pe **Show editor**;
   3. În fereastra nou deschisă alegeți opțiunea **Open script** și navigați către calea de pe disk unde ați salvat scriptul;
   4. Adaugați scriptul;
   5. Executați click pe **Run script**.
![python_basemap](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/03_QGIS_Creare_de_date/Resurse/Img/python_console.png)
   
## Să explorăm datele vector create   

#### Instrumente de explorare a datelor vector
1. **Instrumentul _Identifică_**
    * Executați click pe ![identifica](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/identify.png)
    * Executați click pe un obiect care aparține layer-ului selectat în *Layers Panels*
    * Fereastra deschisă prezintă atributele pentru obiectul respectiv.
2. **Deschiderea tabelului de atribute**
    * Click dreapta pe layer-ul selectat -> Open Attribute Table
3. **Selectarea unui obiect din tabel**
    * Executați click pe numărul rândului din tabel
    > În mod implicit, in QGIS obiectele selectate sunt simbolizate pe hartă cu culoarea **galbenă**.
4. **Selectarea unui obiect din hartă**
    * În *Layers panels* executați click / selectați layer-ul de unde doriți să selectați un obiect;
    * Executați click pe ![](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/select.png);
    * Executați click pe un obiect din hartă care se găsește în layer-ul activ din *Layers Panels*
    * Observați că obiectul selectat are culoarea galbenă. Puteți deschide și tabelul de atribute, iar în căsuța din stânga jos alegeți opțiunea *Show Selected features*
    > Pentru a selecta mai multe obiecte țineți tasta `shift` apăsată.
    > Numărul obiectelor selectate apare și în stânga jos, pe **Status Bar**, lângă **Search Bar**.
5. **Selectarea unui obiect după atribute**
     1. După o valoare;
     2. După o expresie;
6. **Deselectarea obiectelor selectate**
    * Executați click pe ![deselectare](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/deselect.png)
