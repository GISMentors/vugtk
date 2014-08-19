.. _tinyows:

TinyOWS
=======
TinyOWS je projekt postavený na knihovnách MapServeru a poskytuje rozhraní `OGC
WFS <http://opengeospatial.org/standards/wfs>`_ a především WFS-T. 

Konfigurace TinyOWS může být vložena přímo do ``mapfile``, ale kvůli
přehlednosti použijeme druhý způsob - konfiguraci v :download:`samostatném
souboru <../data/tinyows.xml>`.

Jedná se o soubor ve formátu XML. Každý soubor je asociovaný s jedním
připojením do databáze PostgreSQL.

Konfigurace
-----------
Nejprve začneme informacemi o službě a logování. Konfigurační hodnoty jsou
nastaveny v atributech kořenového elementu:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 1-3, 33
Následuje informace o spojení s databází PostgreSQL:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 6,7 
Následují metadata publikovaných služeb:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 9,10 

Kontaktní informace

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 12,14

Nakonec přidáme vrstvy

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 17-23

Všimněte si:

    1. do vrstvy můžeme zapsat ``writeable="1"``
    2. je potřeba nastavit tzv. xml `namespace`
    3. parametrem ``srid=4326,...`` specifikujeme podporované souřadnicový systémy

Úplná dokumentace ke konfiguračním souboru je `dostupná online <http://mapserver.org/tinyows/configfile.html>`_

Test nastavení
--------------
.. note:: Je potřeba obdobným způsobem, jakým jsme nakonfigurovali proměnnou
    prostředí ``MS_MAPFILE`` nakonfigurovat proměnnou ``TINYOWS_CONFIG_FILE``
    viz :ref:`konfigurace-sluzby`.

Opět ve webovém prohlížeči zadáme URL

    http://localhost/cgi-bin/vugtkwfs?service=wfs&request=getcapabilities
 
Měli bychom obdržet::

    <?xml version='1.0' encoding='UTF-8'?>
    <WFS_Capabilities version='1.1.0' updateSequence='0' xmlns='http://www.opengis.net/wfs' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' xmlns:ogc='http://www.opengis.net/ogc' xmlns:gml='http://www.opengis.net/gml' xmlns:ows='http://www.opengis.net/ows' xmlns:xlink='http://www.w3.org/1999/xlink' xsi:schemaLocation='http://www.opengis.net/wfs http://schemas.opengis.net/wfs/1.1.0/wfs.xsd' >
     <ows:ServiceIdentification>

     [...]

    </ogc:Filter_Capabilities>
    </WFS_Capabilities>
