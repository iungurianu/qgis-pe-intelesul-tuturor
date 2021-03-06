![qgis_introducere](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_introducere_logo.png)

## Obiective
* Download și instalare QGIS
* Cunoașterea interfeței QGIS

## Let's jump right in

### Download și instalare QGIS
1. Click [aici](www.qgis.com) .
2. Executați click pe butonul **Download Now**;
3. Descărcați versiunea potrivită pentru sistemul dvs. de operare. Utilizatorii de Windows trebuie să aibă în vedere și versiunea sistemului de operare (32 sau 64 de biți).
> QGIS vă oferă posibilitatea să descărcați 2 versiuni:
> * Versiunea cea mai recentă: **QGIS 3.6** - *la momentul scrierii acestui document*;
> * Versiunea cea mai stabilă și cu suport îndelungat: **QGIS 3.4** - *la momentul scrierii acestui document*;

> Pentru utilizatorii avansați care folosesc platforma Windows, pentru instalare se poate alege și optiunea via **OSGeo4W Network Installer**. Este chiar indicat! Detalii [aici](https://qgis.ro/instaleaza-qgis-profesionist/).

> Pentru utilizatorii de Mac OS X, pentru instalare se poate folosi pachetul dezvoltat de [Lutra Consulting](https://www.lutraconsulting.co.uk/). Îl puteți descărca de [aici](https://lutraconsulting.github.io/qgis-mac-packager/).
> Avantajul folosirii acestui pachet este că conține toate dependințele necesare sub forma unui *standalone installer*.


### Cunoașterea interfeței QGIS

Lansați aplicația QGIS.

![Interfata QGIS](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_creare_de_date_interfata.png)

1. **Bara de meniu**
2. **Toolbar**
3. **Browser Panel**
4. **Layers Panel**
5. **Map Canvas**
6. **Status Bar**
7. **Search Bar**

În **status bar** în casuța de lângă *Coordinate* scrieți **World** și apăsați enter.
![Coordinate](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_coordinate_world.png)
În acest moment ați adăugat în QGIS primul dvs. layer, numit **World Map** (observați că layer-ul apare în *Layers Panels*).
![World_Map](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_world_map.png)


## Explorarea instrumentelor de navigare pe hartă
1. ![pan_map](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/pan.png) - vă permite să navigați pe hartă ținând apăsat butonul stâng al mouse-ului și trăgând în același timp de hartă;
2. ![pan_map_to_selection](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/pan_map_to_selection.png) - mută harta în locația obiectelor selectate fără a schimba nivelul de zoom;
3. ![zoom_in](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom.png) - click pentru *zoom in* un nivel, desenați un dreptungi pentru a face zoom pe o suprafață sau folosiți rotița de la mouse;
4. ![zoom_out](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_out.png) - funcționează ca și *Zoom in*;
5. ![zoom_native](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_to_native.png) - zoom la rezoluția nativă a pixelului
6. ![zoom_to_extent](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_full.png) - zoom la extentul layerelor vizibile încarcate in hartă;
7. ![zoom_to_selection](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_to_selection.png) - zoom la obiectele selectate;
8. ![zoom_to_layer](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_to_layer.png) - zoom la extentul maxim al layer-ului selectat in *Layers Panel*
9. ![zoom_last](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_last.png) - returnează ultimul nivel de zoom;
10. ![zoom_next](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/zoom_next.png) - returnează nivel anterior de zoom;
11. ![new_map_view](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/new_map_view.png) - adaugă o hartă nouă;
12. ![new_bookmark](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/new_bookmark.png) - adaugă un nou semn pe hartă;
13. ![show_bookmark](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/show_bookmark.png) - arată toate semnele existente;
14. ![refresh](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_interfata/refresh.png) - redesenează harta.

## Activarea și dezactivarea Toolbar-urilor
Pentru a activa sau dezactiva **Toolbar-urile** în QGIS executați click-dreapta oriunde este un spațiu alb/nefolosit lângă celelalte toolbar-uri.

![Toolbars](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/toolbars.png)

## Familiarizarea cu Browser-ul
**QGIS Browser** este o structură ierahică care vă permite să navigați către locații de pe calculatorul dvs. direct în QGIS.
![Browser](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/browser.png)

Din **QGIS Browser** puteți aduce date folosind următoarele modalități:
* Click-dreapta -> Add selected layer to canvas
* Dublu-click pe layerul pe care doriți să îl adaugați
* Drag-n-drop din **QGIS Browser** către **Map Canvas**


## Explorați Sistemele de Coordonate
1. Observați că în **Status Bar**, în colțul din stânga jos apare **EPSG:4326**. Sistemul de coordonate este modalitatea prin care QGIS transpune în plan suprafața globului.
2. Executați click pe **EPSG:4326** pentru a deschide fereastra de opțiuni pentru sisteme de coordonate.
![qgis_srs](https://github.com/iungurianu/qgis-pe-intelesul-tuturor/blob/master/02_QGIS_Introducere/Resurse/Img/qgis_srs.png)
> Aceste opțiuni pot fi accesate și din Meniul principal: Project -> Properties -> Alegeți tabul CRS.
3. Fereastra vă oferă opțiuni de căutare a sistemelor de coordonate (de obicei după codul EPSG) și de previzualizarea a zonei unde se aplică sistemul de coordonate.
4. Scrieți în casuța de cautare codul EPSG:3844 corespunzător sistemului de proiecție național. Observați ce se întâmplă în căsuța de previzualizare.
5. Apăsați OK.
6. Observați cum este redat layer-ul **Wold Map**.
> Despre sistemele de coordonate puteți citi mai multe detalii [aici](https://docs.qgis.org/testing/en/docs/user_manual/working_with_projections/working_with_projections.html) sau puteți viziona acest [clip](https://www.youtube.com/watch?v=0vKNo23i8KI) de pe Youtube.

## Salvați proiectul

1. Pentru a salva proiectul QGIS aveți 3 posibilități:
  1. Project - Save 
  2. Folosind combinația de taste CTRL + S
  3. Folosind iconița dedicată din toolbar.
