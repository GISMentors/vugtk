Úvod
----

Vítejte na workshopu *možnosti webových mapových technologií pro "Nové
mapování katastrálního operátu" - I.část* zaměřený na open source GIS
nástroje.

Scénář workshopu
================

Účastník workshopu:

#. spustí na lokálním počítači :doc:`qgis/index`
#. nahraje a zobrazí v QGISu :doc:`vektorová data <qgis/vektor-shp>` ve formátu Esri Shapefile
#. nahraje a zobrazí v QGISu :doc:`rastrová data <qgis/raster-jpg>` ve formátu JPEG, nastaví společný souřadnicový systém
#. nastaví :doc:`symbologii <qgis/symbologie>` mapových vrstev, vektorová data může lokálně :doc:`editovat <qgis/editace>`
#. importuje v prostředí QGIS vektorová data z předešlého bodu do centrální geodatabáze :doc:`postgis/index`
#. zobrazí vektorová data z centrální geodatabáze, nastaví jejich symbologii, data může editovat
#. vypublikuje projekt do lokálně nainstalovaného :doc:`mapového serveru <mapserver/index>`
#. přidá do QGISu :doc:`WMS vrstvu <mapserver/qgis-ws>` z mapového serveru
#. přidá do QGISu :doc:`WFS vrstvu <mapserver/qgis-ws>` z mapového serveru, data může editovat přes WFS-T
#. vytvoří jednoduchou webovou aplikaci pomocí knihovny :doc:`web/leaflet`
#. vytvoří j́ednoduchou webovou aplikaci pomocí knihovny :doc:`web/openlayers`, data může :doc:`editovat <web/openlayers-wfst>` přes WFS-T

Délka workshopu
^^^^^^^^^^^^^^^

* 4 hodiny

Softwarové požadavky
====================

Workshop je koncipován pro následující softwarové balíčky a jejich verze:

* QGIS 2.4, http://qgis.org

  * DB Manager Plugin
  * Spit (Shapefile Import) Plugin


* PostGIS 2.1, http://postgis.net
* MapServer 6.4, http://mapserver.org
* OpenLayers, 2.13, http://openlayers.org
