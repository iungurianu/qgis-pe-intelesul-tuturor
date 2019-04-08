![logo](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/04_QGIS_Verificare_si_validare_topologii/verificare_topologii_logo.png)
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

#### Investigarea integrității layer-ului Bus_stops
1. Click Configure pentru a deschide fereastra Topology Rules Settings. Aici puteți defini a varietate de reguli topologice.
2. Sub *Current Rules* selectați layer-ul Bus_stops. Executați click pe cea de-a doua căsuța pentru a vedea ce reguli sunt disponibile pentru layere de tip punct. Alegeți `must not have duplicates`;
> această regulă se va asigura că nu sunt puncte suprapuse, cu alte cuvinte o stație de autobuz situată peste o alta.
3. Click pe Add Rule;
4. Click OK;
5. În panoul Topology Checker, click Validate All;
> Puteți alege să dați Zoom pe o zonă specifică și să validați topologia doar pentru aceasta zonă executând click pe Validate Extent.
6. Examinați rezultatul.
> Erorile de topologie sunt marcate cu roșu pe hartă.

#### Investigarea integrității layer-ului Bus_routes
1. În panoul Topology Checker executați click pe Configure;
2. Selectați și ștergeți regulile topologice pentru Bus_stops;
3. Creați o nouă regulă pentru Bus_lines folosind `must not have dangles`;
> Această regulă identifică toate punctele de end a unei *dangling line*;
4. Click Add Rule;
5. Click Validate All;
6. Examinați rezultatul;
> Având în vedere că setul de date reprezintă o zonă dintr-un oraș, multe dintre erori sunt la capătul *extent-ului*. Cu toate astea sunt câteva erori și în centru!

**Nu uitați să salvați proiectul!**

