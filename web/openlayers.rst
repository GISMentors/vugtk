OpenLayers
==========

.. image:: ../_static/openlayers.png
    :width: 150px
    :align: right
    :alt: OpenLayers logo

`OpenLayers <http://openlayers.org>`_ je knihovna v jazyce :wikipedia:`JavaScript`, pomocí které
lze vytvářet webové mapové aplikace. Jedná se o velice komplexní knihovnu,
schopnou zobrazovat velké množství formátů dat a služeb, ať už proprietárních,
tak těch postavených na standardech a technických normách.

V současné době se pracuje na zcela nové verzi knihovny `OpenLayers 3
<http://ol3js.org>`_, která se od současné stabilní verze značně liší. Tento
příklad vychází stále ještě ze současné aktuální `OpenLayers 2.13
<http://openlayers.org>`_.

.. note:: Uvedený příklad si můžete `zobrazit v prohlížeči
    <../_static/web/openlayers.html>`_ a vidět tak celý jeho
    zdrojový kód.

.. raw:: html

    <iframe src="../_static/web/openlayers.html" width="620" height="420"></iframe>

Inicializace
------------

Nejdříve musíme připravit webovou stránku, aby obsahovala element s
identifikátorem ``map``, do kterého chceme zobrazit mapu. Dále se potřebujeme
odkázat na knihovnu OpenLayers.

.. note:: Protože zobrazujeme vektorová data, je potřeba použít malý program
    instalovaný na serveru, tzv. "proxy", který požadavky směřující na vzdálený
    server přesměruje ze serveru lokálního. Více viz :wikipedia:`Cross-site scripting`.

    OpenLayers (na rozdíl od :doc:`leaflet`) umožňují kompletní práci
    se souřadnicové systémy na straně klienta (webového prohlížeče). V
    praxi to znamená, že vstupní data mohou být např. v souřadnicové
    systému S-JTSK, ale jsou zobrazeny na podkladové mapě v "web
    mercator" :epsg:`3857`. To je možné díky knihovně `Proj4js
    <http://trac.osgeo.org/proj4js/>`_.  Tato knihovna se ale v
    poslední době značně mění. V její starší verzi *kompatibilní s
    OpenLayers 2* není bohužel korektně implementováno Křovákovo
    zobrazení. Proto se v tomto příkladu odkazujeme na verzi Proj4js
    na `národním geoportálu INSPIRE
    <http://geoportal.gov.cz/web/guest/map>`_.

.. literalinclude:: ../_static/web/openlayers.html
    :language: html
    :lines: 7, 64-66

Po načtení stránky (``onload`` parametry v elementu ``body``), se spustí funkce
``init()``.

Mapa
----

V dalším kroku vytvoříme funkci ``init()``, ve které vytvoříme mapový objekt a
vložíme do připraveného elementu ``map``:

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 13-17

Vrstvy
------

Dále přidáme do mapy dlaždicovanou vrstvu ze zdroje `OpenStreetMap
<http://openstreetmap.org>`_. OpenLayers pro nás mají vrstvu speciálně
připravenou, stačí ji jen použít. Tato vrstva je v OpenLayers brána jako
*základní*, od ní jsou odvozeny některé charakteristiky celé mapy.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 23-28

Mapě byl nastaven pohled se středem o zeměpisných souřadnicích ``50.16, 14.43`` a úroveň přiblížení
je ``13``.

.. note:: V příkladu je vidět, že souřadnice jsou transformovány ze souřadnicovém
    systému WGS-84 (:epsg:`4326`) do souřadnicového systému mapy - což je tzv. Spherical
    Mercator :epsg:`3857`, který se využívá např. ve službě Google Maps.

Dále přidáme letecký snímek námi :ref:`vypublikované služby WMS s leteckým snímkem <mapserver-raster>`.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 30-40

Vrstva WFS
----------

A nakonec :ref:`WFS vrstvu s vektorovými daty budov
<mapserver-vector>` z námi předem nakonfigurované služby WFS.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 42-56

.. rubric:: :secnotoc:`Poznámky`

.. [#f1] Příklady OpenLayers http://openlayers.org/dev/examples/
.. [#f2] Dokumentace OpenLayers http://docs.openlayers.org/
.. [#f3] API dokumentace http://dev.openlayers.org/releases/OpenLayers-2.13.1/doc/apidocs/files/OpenLayers-js.html
