# Poznámky k datům

## RUIAN 

(Okresy, Obce, Ulice, StavebniObjekty; EPSG:5514)

### Esri Shapefile

**Postup pro vytvoření souborů Shapefile ze zdrojových dat:**

        vfr2ogr --type ST_UKSH --format Esri_Shapefile --dsn . --layer Okresy --geom OriginalniHranice

        vfr2ogr --type OB_539058_UKSH --format Esri_Shapefile --dsn . \
        --layer Obce,Ulice,StavebniObjekty --geom OriginalniHranice

viz http://freegis.fsv.cvut.cz/gwiki/RUIAN_/_OGR-VFR#Konverze_do_Esri_Shapefile

### PostGIS

**Postup nahrání předpřipravené dávky:**

         export DB=gismentors_vugtk; dropdb $DB ; createdb $DB && \
         psql $DB -c "create extension postgis; create extension postgis_topology"
         postgis_restore.pl postgis/gismentors_vugtk.dump | psql $DB

**Postup pro vytvoření DB ze zdrojových dat:**

1) vytvoření DB

          export DB=gismentors_vugtk; dropdb $DB ; createdb $DB && \
          psql $DB -c "create extension postgis; create extension postgis_topology"

2) Import ST (Okresy)

          vfr2pg --type ST_UKSH --dbname $DB --layer Okresy --geom OriginalniHranice

3) Import OB (Obce, Ulice, StavebniObjekty)

          vfr2pg --type OB_539058_UKSH --dbname $DB --layer Obce,Ulice,StavebniObjekty --geom OriginalniHranice

4) Vytvoření dávky

         pg_dump -Fc -b -v -Z 9 -O -f postgis/gismentors_vugtk.dump gismentors_vugtk


viz http://freegis.fsv.cvut.cz/gwiki/RUIAN_/_OGR-VFR#Konverze_do_PostGIS

Poznámka: Definice EPSG:5514 v DB obsahuje `+towgs84=570.8,85.7,462.8,4.998,1.587,5.261,3.56`.

