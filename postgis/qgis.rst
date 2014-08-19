Zobrazení dat z geodatabáze PostGIS v QGISu
===========================================

Vektorová data uložená v geodatabázi PostGIS je možné načíst z *menu*

.. figure:: qgis-add-pg-vector-menu.png
           :width: 300px

anebo z *nástrojové lišty* aplikace QGIS.

.. figure:: qgis-add-pg-vector-toolbar.png
           :width: 200px

V dialogu nejprve definuje parametry připojení k databázi.

.. figure:: qgis-postgis-new.png
           :width: 600px

Nastavíme:

* název spojení :fignote:`(1)`
* hostilel (adresa serveru, pokud je to localhost nemusíme vyplňovat) :fignote:`(2)`w
* databáze, ke které se chceme připojit :fignote:`(3)`
* uživatelské jméno a heslo pro připojení k DB :fignote:`(4)`

.. figure:: qgis-postgis-new-settings.png
           :width: 400px

Při opětovném připojení je vhodné si uživatelské jméno a popřípadě i
heslo (v tomto případě bude ale heslo uloženo na lokálním disku v
textovém souboru!) zapamatovat :fignote:`(5)`

.. figure:: qgis-pg-conn-warning.png

Nastavení připojení k databázi nejprve otestujeme :fignote:`(6)` a
poté potvrdíme.

.. figure:: qgis-pg-conn-test.png
            :width: 300px

Poté se můžeme již k databázi připojit

.. figure:: qgis-postgis-connect.png
           :width: 600px

a vybrat vektorové vrstvy :fignote:`(1)`, které chceme z geodatabáze
načíst :fignote:`(2)`.

.. figure:: qgis-postgis-layers.png
           :width: 700px

Alternativní postup (datový katalog)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Připojení k databázi PostGIS je možné definovat i v rámci *datového
katalogu (prohlížeči)*.

.. figure:: qgis-catalog-new.png
            :width: 300px

.. figure:: qgis-postgis-new-settings.png
           :width: 400px

Vektorovou vrstvu z geodatabáze PostGIS přetáhneme z datového katalogu
do okna *Vrstvy*.

.. figure:: qgis-catalog-layer.png
           :width: 700px
