# Scenariu

 Găsirea celei mai optime locații pentru o fabrică!
 
 #### Criterii:
 * Să fie pe teren arabil;
 * Să fie la 500 m de localități (intravilan)
 * Să fie la 5000 m de liniile de înaltă tensiune
 * Să fie la 500 m de drumuri


## Let's jump right in

1.Deschideți QGIS
2.Folosind Browser-ul navigați către locația de pe disk unde ați salvat datele.
3.Adaugați în QGIS **tm_clc2018.shp**
> clc este o prescurtare de la Corine Land Cover. Mai multe detalii găsiți [aici](https://land.copernicus.eu/pan-european/corine-land-cover)
4. Deschideți tabelul de atribute pentru stratul **tm_clc2018.shp**. Observați ca informațiile din tabelul de atribute nu ne ajută să identificăm terenurile arabile sau intravilanele, în forma asta. Vom face un **join**!
5.Din folderul cu date aduceți în QGIS fișierul **clc_descriere.csv**
6.Deschideți tabelul de atribute și observați că și acest fișier conține câmpul **code_18**. Vom folosi acest camp pentru a face legătura cu fișierul **tm_clc2018.shp**
7.În panelul de straturi, executați click dreapta pe **tm_clc2018.shp** -> Properties -> Alegeți tab-ul Joins -> Executați click pe plus (Add new join). La join layer alegeți **clc_descriere**, la join field și target field alegeți **code_18**
8. Bifați căsuța din dreptul **Joined Fields** și alegeți/bifați **descriere**
9. Bifați căsuta din dreptul **Custom Field Name Prefix**, și înlocuiți *clc_descriere_* cu **j_**
> în acest fel orice câmp adăugat în urma *join-ului* va avea prefix-ul j
10. Click OK.
11. Click OK pentru a închide fereastra de Layer Properties.
12. Deschideți din nou tabelul de atribute pentru fișierul **tm_clc2018.shp** și observați apariția câmpului nou **j_descriere**
> Join-ul nu este permanent. Este o operațiune activă atâta timp cât proiectul QGIS este deschis. Pentru face stratul permanentul executați click dreapta -> Export -> Save features as
