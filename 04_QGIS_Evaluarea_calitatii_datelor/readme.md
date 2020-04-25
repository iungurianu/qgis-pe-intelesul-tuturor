
![logo](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/04_QGIS_Verificare_si_validare_topologii/verificare_topologii_logo.png)
Laborator preluat de la [Geoacademy](http://spatialquerylab.com/foss4g-academy-curriculum/)
## Scenariu
**Lucrați ca analist GIS pentru orașul Albuquerque, New Mexico, iar sarcina dvs. este să verificați și să validați un set de date înainte de a fi publicat pe geo-portalul orașului.**

## Obiective
* Verificarea calității datelor vector cu ajutorul regulilor topologice

## Let's jump right in
### Data
1. Creați un folder nou intr-o locație pe disk, numit `QGIS_Topologie`.
2. Download [data](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/tree/master/04_QGIS_Verificare_si_validare_topologii/Data) și salvați în folder-ul nou creat.
### QGIS at work
1. Deschideți QGIS 3.4. navigați către locația folderului `QGIS_Topologie` și adăugați fișierele următoare: **parcels.shp**, **Bus_stops.shp** și **Bus_routes.shp**;
2. Salvați proiectul: Project -> Save -> `QGIS_Topologie.qgz`;
3. Din bara de meniu, alegeți Plugins -> Manage and Install Plugins;
4. Selectați tab-ul Installed și activați plugin-ul **Topology Checker**;
5. Click Vector -> Topology Checker pentru a deschide panoul Topology Checker;
### Verificarea integrității datelor
****
##### Verificarea integrității layer-ului Bus_stops
1. Click *Configure* pentru a deschide fereastra *Topology Rules Settings*. Aici puteți defini a varietate de reguli topologice.
2. Sub *Current Rules* selectați layer-ul Bus_stops. Executați click pe cea de-a doua căsuța pentru a vedea ce reguli sunt disponibile pentru layere de tip punct. Alegeți `must not have duplicates`;
> Această regulă se va asigura că nu sunt puncte suprapuse, cu alte cuvinte o stație de autobuz situată peste o alta.
3. Click pe *Add Rule*;
4. Click OK;
5. În panoul *Topology Checker*, executați click pe *Validate All*;
> Puteți alege să dați Zoom pe o zonă specifică și să validați topologia doar pentru aceasta zonă executând click pe *Validate Extent*.
6. Examinați rezultatul.
> Erorile de topologie sunt marcate cu roșu pe hartă.

##### Verificarea integrității layer-ului Bus_routes
1. În panoul *Topology Checker*, executați click pe *Configure*;
2. Selectați și ștergeți regulile topologice pentru Bus_stops;
3. Creați o nouă regulă pentru Bus_lines folosind `must not have dangles`;
> Această regulă identifică toate punctele de end a unei *dangling line*;
4. Click *Add Rule*;
5. Click *Validate All*;
6. Examinați rezultatul;
> Având în vedere că setul de date reprezintă o zonă dintr-un oraș, multe dintre erori sunt la capătul *extent-ului*. Cu toate astea sunt câteva erori și în centru!

**Nu uitați să salvați proiectul!**

##### Verificarea integrității layer-ului parcels
1. În panoul *Topology Checker*, executați click pe *Configure*;
2. Selectați și ștergeți orice regulă existentă;
3. Alegeți 3 reguli: `must not have gaps`, `must not overlap` și `must not have duplicates`;
4. Click OK;
5. În panoul *Topology Checker*, executați click pe *Validate All*.
6. Examinați rezultatul

## :exclamation:Este timpul pentru o :beer: sau o :coffee:. Luați o pauză de 5 minute!

### Rezolvarea erorilor de topologie
****
#### Ne vom focusa pe layer-ul parcels
 ##### Rezolvarea erorilor cauzate de geometrii duplicate
1. Revalidați regulile de topologie pentru layer-ul parcels;
2. Executați dublu-click pe prima eroare din tabelul din panelul *Topology Checker* pentru a afișa pe hartă locația erorii;
3. Folosiți unealta *Select Feature by Rectangle* și desenați un dreptunghi mic prin care să selectați parcelele dublate;
4. Executați Click dreapta -> Open Attribute Table;
5. În căsuța din stânga-jos alegeți opțiunea: *Show Selected Features*;
6. Observați că pentru cele doua obiecte selectate atributele sunt identice;
7. Selectați unul dintre obiecte (de obicei se alege obiectul cu id-ul cel mai mare), executând click pe numărul rândului;
8. Porniți editarea, executând click pe *Toggle Editing Mode*;
> Dacă aveți tabelul de atribute deschis, puteți porni editarea pentru layer-ul respectiv folosind și combinația de taste `CTRL+E`:
9. Cu editarea pornită, executați click pe butonul *Delete Selected Features*
10. Repetați pașii pentru restul erorilor rămase.

>O altă abordare este să folosiți și algoritmul **Delete duplicate geometries** din **Processing Toolbox** - mult mai potrivită pentru rezolvarea unui număr mare de erori!

##### Rezolvarea erorilor cauzate de suprapuneri

 Pentru a rezolva aceste erori trebuie să activăm snapping-ul pentru a face editarea mult mai ușoară;
 
 *Activarea snapping*
 
1. Din bara de menu alegeți View -> Toolbars -> Activați Snapping Toolbar (o nouă bară de instrumente va fi disponibilă în QGIS);
2. Executați click pe butonul *Enable snapping* din bara de snapping sau apăsați tasta **S** pentru a activa snapping-ul;
3. Executați click pe cel de-al doilea buton din bara de snapping și alegeți opțiunea: *Open Snapping Option*;
4. În fereastra nou deschisă, executați click pe cel de-al doilea buton și alegeți opțiunea *Advanced Configuration*;
5. Bifați casuta din stanga pentru toate cele 3 layere;
6. Pentru layer-ul **parcels** alegeți la *Type* - **vertex**, la *Tolerance* introduceți valoarea **10**, iar la *Units* alegeți **meters**
7. Bifați *Enable Topological Editing*;
8. Bifați *Enable snapping on intersection*;
> Editarea topologică menține granițele comune în mozaicurile poligonale. Cu această opțiune verificată, QGIS detectează o limită comună într-un mozaic de poligon și trebuie doar să mutați vertex-ul o singură dată, iar QGIS va avea grijă să actualizeze cealaltă limită!
9. Închideți fereastra de snapping
10. Din bara de menu, alegeți Settings -> Options și executați click pe tab-ul *Digitizing Tools*;
11. Qgis pune by default valoarea **10 pixeli** pentru *Search radius for vertex edits*. Asigurați-vă că așa este!
> Setarea acestui lucru cu o valoare diferită de 0 garantează că QGIS găsește vertexul corect când se editează!
12. Click OK pentru a închide fereastra.

 *Rezolvarea erorilor de suprapunere*
1. Executați click dreapta pe layer-ul **parcels** -> Properties click pe tab-ul *Symbology* și setați opacitatea la 50%;
2. Click OK pentru a închide fereastra.
3. În panelul *Topology Checker* debifați *Show Errors*;
4. Executați dublu click pe eroarea cu *Feature ID 624*. Harta va afișa automat locația acestei erori. Cu erorile de topologie debifate și cu opacitatea setată erorile de suprapunere se pot observa ușor.
5. Porniți editarea, executând click pe *Toggle Editing Mode*;
6. Folosiți unealta *Select Feature by Rectangle* și selectați parcela din stânga. **Vertecșii parcelei selectate vor apărea cu X de culoare roșie**;
7. În toolbarul *Digitizing*, executați click pe unealta *Vertex Tool (Current layer)*. Această unealtă vă permite să mutați vertecși individual pentru layer-ul selectat in *Layers Panel*.
8. Executați click pe un vertex-ul din colțul din dreapta sus al parcelei și mutați-l până când se lipește de limita parcelei cu care se suprapune.
9. Repetați același proces și pentru vertex-ul din colțul din dreapta jos.
10. În panelul *Topology Checker*, executați click pe *Validate All* și observați că această eroare nu mai apare în lista nou generată.
11. Puteți rezolva și celelalte erori de suprapunere în același mod.

##### Rezolvarea erorilor cauzate de spațiile goale
1. În panelul *Topology Checker*, executați click pe prima eroare de tip *Gap*;
2. În panelul *Topology Checker*, debifați *Show Errors*;
3. Selectați parcela aflată la Nord și executați click pe *Vertex Tool (Current layer)*;
4. Selectați vertex-ul din partea de Sud-Vest a parcelei selectate. Mutați-l până se lipește de vertex-ul parcelei din Sud, închizănd astfel spațiul gol.
5. Executați click pe *Validate extent* pentru a avea confirmarea că eroarea a fost rezolvată;
6. Puteți rezolva și celelalte erori în acest mod.

La final, nu uitați să salvați modificările făcute!

> Utilizarea algoritmului **v.clean** din suita Grass poate rezolva în mod automat o serie de erori topologice. Mai multe detalii [aici](https://grass.osgeo.org/grass77/manuals/v.clean.html)

**Ați finalizat cu succes sesiunea de Verificare și validare topologii** :+1:. 
Mergeți la următoarea [sesiune](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/tree/master/05_QGIS_Analiza_vector)


 
