.. _tinyows:

TinyOWS
=======

`TinyOWS <http://mapserver.org/tinyows/>`_ je projekt postavený na
knihovnách MapServeru a poskytuje rozhraní `OGC WFS
<http://opengeospatial.org/standards/wfs>`_ a především WFS-T.

Konfigurace TinyOWS může být vložena přímo do ``mapfile``, ale kvůli
přehlednosti použijeme druhý způsob - konfiguraci v :download:`samostatném
souboru <../data/tinyows.xml>`.

Jedná se o soubor ve formátu :wikipedia:`XML`. Každý soubor je
asociovaný s jedním připojením do databáze PostgreSQL.

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
Dále metadata publikovaných služeb:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 9,10 

Kontaktní informace:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 12,14

Nakonec přidáme vrstvy:

.. literalinclude:: ../data/tinyows.xml
   :language: xml
   :lines: 17-23

Všimněte si, že:

    1. do vrstvy můžeme zapsat ``writeable="1"``
    2. je potřeba nastavit tzv. xml `namespace`
    3. parametrem ``srid=4326,...`` specifikujeme podporované souřadnicový systémy

Úplná dokumentace ke konfiguračnímu souboru je `dostupná online <http://mapserver.org/tinyows/configfile.html>`_

Test nastavení
--------------
.. note:: Je potřeba nakonfigurovat proměnnou ``TINYOWS_CONFIG_FILE`` - obdobným způsobem, jakým jsme nakonfigurovali proměnnou
    prostředí ``MS_MAPFILE`` (viz :ref:`konfigurace-sluzby`).

Opět ve webovém prohlížeči zadáme URL:

    http://localhost/cgi-bin/vugtkwfs?service=wfs&request=getcapabilities
 
Měli bychom obdržet::

    <?xml version='1.0' encoding='UTF-8'?>
    <WFS_Capabilities version='1.1.0' updateSequence='0' xmlns='http://www.opengis.net/wfs' .. >
     <ows:ServiceIdentification>

     [...]

    </ogc:Filter_Capabilities>
    </WFS_Capabilities>
