Poznámky k datům
================

Okresy (EPSG:5514)
------------------

        vfr2ogr --type ST_UKSH --format Esri_Shapefile --dsn . --layer Okresy --geom OriginalniHranice

viz http://freegis.fsv.cvut.cz/gwiki/RUIAN_/_OGR-VFR#Konverze_do_Esri_Shapefile

Poznámka ke QGISu: Ve verzi 2.4 přidá automaticky
`+towgs84=589,76,480,0,0,0,0` (?). Pro ČR nutno upravit na
`+towgs84=570.8,85.7,462.8,4.998,1.587,5.261,3.56`.