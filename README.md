Workshop možnosti webových mapových technologií pro Nové mapování katastrálního operátu - I.část
================================================================================================

Kompilace dokumentace
--------------------------------

        git clone git@github.com:GISMentors/sphinx-template.git
        git clone git@github.com:GISMentors/vugtk.git
        cd vugtk
        make html

Scénář
-------

- uživatel spustí QGIS
- nahraje a zobrazí v QGISu vektorová data ve formátu ESRI Shapefile, nastaví jejich symbologii, data může lokálně editovat
- nahraje v prostředí QGIS vektorová data z předešlého bodu do centralní geodatabáze PostGIS
- zobrazí vektorová data z centralní geodatabáze, nastaví jejich symbologii, data může editovat
- vypublikuje projekt do centralně nainstalovaného mapového serveru
- přidá do QGISu WMS vrstvu z mapového serveru
- přidá do QGISu WFS vrstvu z mapového serveru
- vytvoří jednoduchou webovou aplikaci pomocí knihovny OpenLayers
- vytvoří jednoduchou webovou aplikaci pomocí knihovny Leaflet

Zdrojová data
-------------

- data RÚIAN ve formátu Esri Shapefile a PostGIS
- ortofoto ČR ve formátu JPEG

Všechna použitá data jsou v souřadnicovém systému S-JTSK (EPSG:5514).

Délka
-----

- 4 hodiny

Software
--------

- Pracovní stanice účastníků: QGIS 2.4, QGIS OpenGeo Suite plugin, MapServer 6.4
- Centrální server VÚGTK: PostGIS 2.1, MapServer 6.4
