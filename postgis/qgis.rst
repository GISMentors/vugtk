Zobrazení dat z geodatabáze PostGIS v QGISu
===========================================

Vektorová data uložená v geodatabázi PostGIS je možné načíst z *menu*

.. figure:: qgis-add-pg-vector-menu.png
           :width: 300px

anebo z *nástrojové lišty* aplikace QGIS. Další možností je použít
:ref:`datový katalog <DataCatalog>`.

.. figure:: qgis-add-pg-vector-toolbar.png
           :width: 200px

V dialogu nejprve nadefinujeme parametry připojení k databázi.

.. figure:: qgis-postgis-new.png
           :width: 600px

Nastavíme:

* název spojení :fignote:`(1)`
* hostitel (adresa serveru, pokud je to localhost, nemusíme vyplňovat) :fignote:`(2)`
* databáze, ke které se chceme připojit :fignote:`(3)`
* uživatelské jméno a heslo pro připojení k databázi :fignote:`(4)`

.. figure:: qgis-postgis-new-settings.png
           :width: 400px

Pro opětovné připojení je vhodné si uživatelské jméno a popřípadě i
heslo (v tomto případě bude heslo uloženo na lokálním disku v textovém
souboru!) uložit :fignote:`(5)`

.. figure:: qgis-pg-conn-warning.png

Nastavení připojení k databázi nejprve otestujeme :fignote:`(6)` a
poté potvrdíme.

.. figure:: qgis-pg-conn-test.png
            :width: 300px

Následně se již můžeme k databázi připojit

.. figure:: qgis-postgis-connect.png
           :width: 600px

a vybrat vektorové vrstvy :fignote:`(1)`, které chceme z geodatabáze
načíst :fignote:`(2)`.

.. figure:: qgis-postgis-layers.png
           :width: 700px

.. _DataCatalog:

Alternativní postup (datový katalog)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Připojení k databázi PostGIS je možné definovat i v rámci *datového
katalogu (prohlížeče)*.

.. figure:: qgis-catalog-new.png
            :width: 300px

.. figure:: qgis-postgis-new-settings.png
           :width: 400px

Vektorovou vrstvu z geodatabáze PostGIS přetáhneme z datového katalogu
do okna *Vrstvy*.

.. figure:: qgis-catalog-layer.png
           :width: 700px
