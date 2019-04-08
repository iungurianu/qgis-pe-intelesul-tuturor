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
5. Click Vector -> Topology Checker 
    
