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
7. În fereastra *Georeferencer*, executați click pe *Open raster* și navigați către ...`\QGIS_Creare_date\Date\Raster\variante_centura_tm.jpg`
> Examinați imaginea, încercați să gasiți elemente care să vă ajute la georeferențiere.
8. Minimizați fereastra *Georeferencer* și mergeți înapoi în fereastra principală QGIS;
9. Executați click pe *Open Data Manager*, asigurați-vă că tab-ul *Vector* este selectat și navigați către ...`\QGIS_Creare_date\Date\Vector\ancpi_uat.shp`;
> Pentru a deschide *Open Data Manager* puteți folosi și combinația de taste **CTRL+L**;
10. În acest moment aveți deschise in QGIS, un subset al limitelor de unități administrativ teritoriale (UAT) corespunzator zonei înconjurătoare a municipiului Timișoara;
11. Executați click dreapta pe layer -> Properties și selectați tab-ul *Labels*;
> Puteți activa panoul *Layer Styling* prin apăsarea tastei **F7**
12. Schimbați din *No labels* în *Single labels*;
13. În casuța *Label with* alegeți coloana *DE ADAUGAT!!!*
14. Vom georeferenția imaginea cu ajutorul limitelor de UAT;
15. Maximizația fereastra *Georeferencer* și observați că butonul *Add Point* este deja activat;
16. Pe imaginea ce urmează a fi georeferențiată, limitele de UAT sunt simbolizate cu linie punctată de culoare maro;
17. Executați zoom către colțul din stânga al imaginii, la limita dintre Săcălaz și Timișoara și adăugați un punct unde limita își schimbă direcția;
18. În fereastra *Enter Map Coordinates*, executați click pe butonul *From map canvas*;
19. Faceți zoom spre punctul comun și executați click.
20. În fereastra *Enter Map Coordinates*, observați că sunt trecute valorile coordonatelor. Apăsați OK.
21. Observați că punctul nou adăugat este marcat cu roșu pe imaginea ce urmează să fie georeferențiață și că apare și în tabelul *GCP table*;
22. Repetați procesul și încercați să mai adaugați cel puțin 3 puncte, situate în colțurile imaginii.
> După adăugarea a cel puțin 4 puncte, în tablul *GCP table*, în rubrica *Residual(pixels)* sunt trecute erorile de georeferențiere. Încercați să adăugați puncte astfel încât să minimizați valorile erorilor.
23. La final, în fereastra de *Georeferencer* executați click pe *Transformation Settings*;
24. La *Transformation type* alegeți **Polynomial 1**, pentru *Resampling method* alegeți **Nearest neighbour**;
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
3. La *Geometry type* selectați *Line*;
4. Pentru sistemul de coordonate alegeți *EPSG:3844*;
5. Dacă doriți să adaugați atribute, puteți completa rubrica *Name* cu numele câmpului, la *Type* să alegeți tipul acestuia și în final să executați click pe *Add to Fields List*;
6. Click OK.
7. Observați că layer-ul nou creat apare in *Layer Panels*.

> Pașii de mai sus sunt identici pentru crearea obiectelor de tip punct, linie sau poligon. Singura diferență fiind la *pasul 3* unde se alege **tipul geometriei**!
