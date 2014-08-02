Poznámky k datům
================

Esri Shapefile (Okresy; EPSG:5514)
----------------------------------

        vfr2ogr --type ST_UKSH --format Esri_Shapefile --dsn . --layer Okresy --geom OriginalniHranice

viz http://freegis.fsv.cvut.cz/gwiki/RUIAN_/_OGR-VFR#Konverze_do_Esri_Shapefile

Poznámka ke QGISu: Ve verzi 2.4 přidá automaticky
`+towgs84=589,76,480,0,0,0,0` (?). TODO: Pro ČR nutno upravit na
`+towgs84=570.8,85.7,462.8,4.998,1.587,5.261,3.56`.

PostGIS (Okresy, Obce, Ulice, StavebniObjekty; EPSG:5514)
---------------------------------------------------------

1) vytvoření DB

 export DB=ruian_vugtk; dropdb $DB ; createdb $DB && psql $DB -c "create extension postgis"

2) Import ST (Okresy)

 vfr2pg --type ST_UKSH --dbname $DB --layer Okresy --geom OriginalniHranice

3) Import OB (Obce, Ulice, StavebniObjekty)

 vfr2pg --type OB_539058_UKSH --dbname $DB --layer Obce,Ulice,StavebniObjekty --geom OriginalniHranice

viz http://freegis.fsv.cvut.cz/gwiki/RUIAN_/_OGR-VFR#Konverze_do_PostGIS

Poznámka: Definice EPSG:5514 v DB obsahuje `+towgs84=570.8,85.7,462.8,4.998,1.587,5.261,3.56`.

Vytvoření dávky:

 pg_dump -Fc -b -v -x -Z 9 -f ruian_vugtk.dump ruian_vugtk

Nahrání dávky do DB:

 export DB=ruian_vugtk_cpy; dropdb $DB ; createdb $DB && psql $DB -c "create extension postgis"
 postgis_restore.pl ruian_vugtk.dump | psql $DB
