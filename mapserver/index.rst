MapServer
=========

.. image:: ../_static/mapserver.png
    :width: 300px
    :align: right
    :alt: MapServer logo

`MapServer <http://mapserver.org>`_ patří mezi nejstarší open source projekty
pro GIS. Původně byl vyvíjen americkým úřadem pro letectví a vesmír (NASA),  ale
v současnosti je zcela v rukou komunity. V opakovaných měřeních vychází jako
nejrychlější mapový server ve světě otevřeného software [#f1]_.

MapServer je tradičně používaný v české veřejné správě (např. mapový server
ÚHÚL, nahlížení do katastru nemovitostí, obecní mapové portály), je velice
oblíbený českými firmami poskytujícími webové GIS řešení.

Konfigurace MapServeru
----------------------
MapServer nedisponuje žádným grafickým uživatelským rozhraním. Až na
výjimky [#f2]_ se konfiguruje pomocí jednoduchého textového souboru, který je
velice dobře dokumentován na `na webových stránkách <http://mapserver.org/mapfile/index.html>`_.

Jednotlivé konfigurační sekce jsou započaty klíčovým slovem a ukončeny slovem
``END``. Je lhostejno, používáte-li velká či malá písmena nebo nepoužíváte-li
odsazení jednotlivých sekcí. Pro větší čitelnost se ale doporučuje používate
``VELKÁ PÍSMENA`` v jednolivých sekcích a používat odsazení.

Celý příklad *mapfile* si můžete `prohlídnout v souboru <../data/vugtk.map>`_. 

Mapfile začíná slovem ``MAP`` a je ukončem zmiňovaným ``END``, v ůvodní sekci
jsou základní údaje o projektu:

.. literalinclude:: ../data/vugtk.map
   :lines: 1-7, 106

Je důležité nakonfigurovat výchozí souřadný systém projektu, použijeme k tomu
EPSG kód pro S-JTSK.

.. literalinclude:: ../data/vugtk.map
   :lines: 25-27

Neméně důležitá jsou metadata pro služby OWS a konfigurační cesty ke vznikajícím obrázkům:

.. literalinclude:: ../data/vugtk.map
   :lines: 12-23

Následuje konfigurace vrstev. Jako příklad uvedeme nejprve rastrovou vrstvu z
připraveného lokálně uloženého rastrového souboru.

.. literalinclude:: ../data/vugtk.map
   :lines: 29-40

Všiměte si, že rastrový snímek je v jiném souřadném systému, než celý projekt
(UTM vs. S-JTSK).
   
.. rubric:: Poznámky

.. [#f1] Prezentace o porovnání různých mapových serverů http://www.slideshare.net/gatewaygeomatics.com/wms-performance-shootout-2011
.. [#f2] MapServer lze využít ve vlastích programech díky API, potom je
  konfigurace vyřešena přímo v programu a ne v externím konfiguračním souboru.
