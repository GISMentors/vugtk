Leaflet
=======
.. image:: ../_static/leaflet-logo.png
    :width: 300px
    :align: right
    :alt: Leaflet logo

`Leaflet <http://leafletjs.com/>`_ je knihovna v jazyce :wikipedia:`JavaScript`, pomocí které
lze vytvářet webové mapové aplikace. Na rozdíl od :doc:`openlayers` je to spíše
knihovna lehká, určená pro jednodušší aplikace. To ji ovšem nijak
nediskvalifikuje pro specifické případy použití.

.. note:: Uvedený příklad si můžete `zobrazit v prohlížeči
    <../_static/web/leaflet.html>`_ a vidět tak celý jeho
    zdrojový kód.

.. raw:: html

    <iframe src="../_static/web/leaflet.html" width="620" height="420"></iframe>

Inicializace
------------

Nejdříve musíme připravit webovou stránku, aby obsahovala element s
identifikátorem ``map``, do kterého chceme zobrazit mapu. Dále se potřebujeme
odkázat na knihovnu Leaflet.

.. literalinclude:: ../_static/web/leaflet.html
    :language: html
    :lines: 7,10,12

Mapa
----

V dalším kroku vytvoříme mapový objekt a vložíme ho do připraveného elementu
``map``.

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 15-16

Mapě byl nastaven pohled se středem na zeměpisných souřadnicích ``50.16, 14.43`` a úroveň přiblížení ``12``.


Vrstvy
------

Přidáme do mapy dlaždicovanou vrstvu ``tileLayer``.

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 18-22

Dále přidáme letecký snímek námi :ref:`vypublikované služby WMS s leteckým snímkem <mapserver-raster>`.

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 28-33

A nakonec :ref:`WMS vrstvu s vektorovými daty budov <mapserver-vector>`.

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 36-42

.. note:: Jak již bylo řečeno, Leaflet je ve své podstatě jednoduchá
    knihovna, jejíž cíl není přizpůsobit se požadovaným datům a ty
    "nějak" zobrazit. Jde o knihovnu, která vyžaduje data určitým
    způsobem předzpracovaná a ty následně zobrazuje velice dobře na
    většině myslitelných zařízeních.

    Leaflet nepodporuje standard OGC WFS, i když má skvělou podporu
    pro zobrazování vektorových dat. Ty ale nemohou přicházet ve
    formátu :wikipedia-en:`GML <Geography Markup Language>` (dle
    standardu OGC WFS), ale nejlépe ve formátu
    :wikipedia-en:`GeoJSON`.

Vrstva WFS
----------

Přidáme vektorovou vrstvu z našeho WFS serveru. Data musí být nejprve načtena ze
serveru a až poté můžeme vrstvu vytvořit. Nemůžeme se odkázat na WFS server
přímo s dotazem ``GetFeature``, protože pravděpodobně narazíme na problém s
různými doménami (viz :wikipedia:`Cross-site scripting`). Proto budeme postupovat přes
již vytvořený skript (``proxy``).

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 45-61

Další typy vrstev a vstupních dat, stejně jako detaily ke konfiguraci a
možnostem Leafletu, si můžete prohlídnout v příkladech [#f1]_ nebo dokumentaci [#f2]_.

.. rubric:: :secnotoc:`Poznámky`

.. [#f1] Příklady Leaflet http://leafletjs.com/examples.html
.. [#f2] Dokumentace Leaflet http://leafletjs.com/reference.html
