OpenLayers
==========

`Leaflet <http://openlayers.org>`_ je knihovna v jazyce JavaScript, pomocí které
lze vytvářet webové mapové aplikace. Jedná se o velice komplexní knihovnu,
schopnou zobrazovat velké množství formátů dat a služeb, ať už proprietárních,
tak standardních.

V současné době se pracuje na zcela nové verzi knihovny `OpenLayers 3
<http://ol3.js.org>`_, která se od současné stabilní verze značně liší. Tento
příklad vychází stále ještě ze současné aktuální `OpenLayers 2.13
<http://openlayers.org>`_.

.. note:: Uvedený příklad si můžete `zobrazit v prohlížeči
    <../_static/web/openlayers.html>`_ a vidět tak celý jeho
    zdrojový kód.

.. raw:: html

    <iframe src="../_static/web/openlayers.html" width="620" height="420"></iframe>

Nejdříve musíme připravit webovou stránku, aby obsahovala element s
identifikátorem ``map``, do kterého chceme zobrazit mapu. Dále se potřebujeme
odkázat na knihovnu OpenLayers.

.. note:: Protože zobrazujeme vektorová data, je potřeba použít malý program
    instalovaný na serveru, tzv. "proxy", která požadavky směřující na vzdálený
    server přesměruje ze serveru lokálního. Více viz :wikipedia:`Cross-site_scripting <Cross-site_scripting>`

.. literalinclude:: ../_static/web/openlayers.html
    :language: html
    :lines: 7-9, 63-65

Po načtení stránky (``onload`` parametry v elementu ``body``), se spustí funkce
``init()``.

V dalším kroce vytvoříme funkci ``init()``, ve které vytvoříme mapový objekt a
vložíme do připraveného elementu ``map``:

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 13-17

Dále přidáme do mapy dlaždicovanou vrstvu ze zdroje `OpenStreetMap
<http://openstreetmap.org>`_. OpenLayers pro nás mají vrstvu speciálně
připravenou, stačí ji jen použít. Tato vrstva je v OpenLayers brána jako
**základní**, od ní jsou odvozeny některé charakteristiky celé mapy.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 23-28

Mapě byl nastaven pohled se středem na souřadnicích 50.16, 14.43 a úroveň přiblížení
je 13.

.. note:: V příkladu je vidět, že souřadnice jsou transformovány ze souř.
    systému WGS84 do souřadnicového systému mapy - což je tzv. Spherical
    Mercator EPSG:3857, který se využívá např. ve službě Google Maps.

Dále přidáme letecký snímek námi vypublikované služby WMS s leteckým snímkem

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 30-40

A nakonec vrstvu WFS s vektorovými daty budov z námi předem nakonfigurované
služby WFS.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 42-56

Editace pomocí protokolu WFS-T
------------------------------

.. note:: Nastavení editace vektorových dat pomocí protokolu WFS-T vyžaduje již
    určité programátorské schopnosti. Tento příklad berte pouze jako
    ilustrativní, pro reálný systém je potřeba ošetřit celou řadu krajních
    případů.

.. raw:: html

    <iframe src="../_static/web/openlayers-wfst.html" width="620" height="420"></iframe>

Editace pomocí protokolu WFS-T (transakční WFS) vyžaduje jednak nastavení na
straně serveru a jednak přidání editačních nástrojů do projektu OpenLayers.
Pokračovat budeme na předchozím příkladě, ale poněkud jej rozšíříme, verzi s
WFS-T si můžete prohlédnout `dalším příkladě <../_static/web/openlayers-wfst.html>`_.

Nejprve přidáme do seznamu strategií u vrstvy WFS strategii pro ukládání:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 66-86
   :emphasize-lines: 74

Přidáme nástroje pro kreslení nových prvků a změnu existujících prvků v mapě:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 90-99

Nyní vytvoříme funkci, která má být zavolána a která pošle změněná vektorová data na
server pomocí protokolu WFS-T. Funkce zruší výběr všech prvků a podešle obsah
mapy na server.

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 101-110

Nakonec vyrobíme tlačítko, které tuto ukládací funkci zavolá:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 112-119

.. rubric:: Poznámky

.. [#f1] Příklady OpenLayers http://openlayers.org/dev/examples/
.. [#f2] Dokumentace OpenLayers http://docs.openlayers.org/
.. [#f3] API dokumentace http://dev.openlayers.org/releases/OpenLayers-2.13.1/doc/apidocs/files/OpenLayers-js.html
