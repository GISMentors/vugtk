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

Nejdříve musíme připravit webovou stránku, aby obsahovala element s
identifikátorem ``map``, do kterého chceme zobrazit mapu. Dále se potřebujeme
odkázat na knihovnu OpenLayers.

.. literalinclude:: ../_static/web/openlayers.html
    :language: html
    :lines: 7,10-11

V dalším kroku vytvoříme mapový objekt a vložíme do připraveného elementu
``map``:

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 14-18

.. todo:: souřadnice 

Mapě byl nastaven pohled se středem na souřadnicích 50, 14 a úroveň přiblížení
je 13.

Dále přidáme do mapy dlaždicovanou vrstvu ze zdroje `OpenStreetMap
<http://openstreetmap.org>`_. OpenLayers pro nás mají vrstvu speciálně
připravenou, stačí ji jen použít.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 20-22

Dále přidáme letecký snímek námi vypublikované služby WMS s leteckým snímkem

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 24-30

A nakonec vrstvu WFS s vektorovými daty.

.. todo:: jakými daty popsat 

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 32-45

Editace pomocí protokolu WFS-T
------------------------------

.. note:: Nastavení editace vektorových dat pomocí protokolu WFS-T vyžaduje již
    určité programátorské schopnosti. Tento příklad berte pouze jako
    ilustrativní, pro reálný systém je potřeba ošetřit celou řadu krajních
    případů.

Editace pomocí protokolu WFS-T (transakční WFS) vyžaduje jednak nastavení na
straně serveru a jednak přidání editačních nástrojů do projektu OpenLayers.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 47-49

Nyní vytvoříme funkci, která má být zavolána a která pošle změněná vektorová data na
server pomocí protokolu WFS-T.

.. literalinclude:: ../_static/web/openlayers.html
   :language: javascript
   :lines: 47-49

.. rubric:: Poznámky

.. [#f1] Příklady OpenLayers http://openlayers.org/dev/examples/
.. [#f2] Dokumentace OpenLayers http://docs.openlayers.org/
.. [#f3] API dokumentace http://dev.openlayers.org/releases/OpenLayers-2.13.1/doc/apidocs/files/OpenLayers-js.html
