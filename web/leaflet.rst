Leaflet
=======
.. image:: ../_static/leaflet-logo.png
    :width: 300px
    :align: right
    :alt: Leaflet logo

`Leaflet <http://leafletjs.com/>`_ je knihovna v jazyce JavaScript, pomocí které
lze vytvářet webové mapové aplikace. Na rozdíl od OpenLayers je to spíše
knihovna lehká, určená na méně funkční aplikace. To ji ovšem nijak
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

V dalším kroce vytvoříme mapový objekt a vložíme do připraveného elementu
``map``:

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 15-16

Mapě byl nastaven pohled se středem na souřadnicích 50.14, 14.43 a úroveň přiblížení
je 13.


Vrstvy
------

Dále přidáme do mapy dlaždicovanou vrstvu ``tileLayer``

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 18-22

Dále přidáme letecký snímek námi vypublikované služby WMS s leteckým snímkem

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 28-33

A nakonec WMS vrstvu s vektorovými daty budov.

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 36-42

.. note:: Jak bylo řečeno, Leaflet je ve své podstatě jednoduchá knihovna, resp.
    knihovna, jejíž cíl není přizpůsobit se požadovaným datům a ty "nějak"
    zobrazit, ale knihovna, která vyžaduje data určitým způsobem předzpracovaná
    a ty následně zobrazuje velice dobře na většině myslitelných zařízeních.

    Leaflet nepodporuje standard OGC WFS, i když má skvělou podporu pro
    zobrazování vektorových dat. Ty ale nemohou přicházet ve formátu GML, ale
    nejlépe ve formátu GeoJSON.

Vrstva WFS
----------

Přidáme vektorovou vrstvu z našeho WFS serveru. Data musí být jeprve načtena ze
serveru a až poté můžeme vrstvu vytvořit. Nemůžeme se odkázat na WFS server
přímo s dotazme ``GetFeature``, protože pravděpodobně narazíme na problém s
různými doménami :wikipedia:`Cross-site_scripting <Cross-site_scripting>`, proto budeme postupovat přes
už vytvořený skript (``proxy``).

.. literalinclude:: ../_static/web/leaflet.html
   :language: javascript
   :lines: 45-61

Další typy vrstev a vstupních dat, stejně jako detaily ke konfiguraci a
možnostem Leafletu, si můžete prohlídnout v příkladech [#f1]_ nebo dokumentaci [#f2]_.

.. rubric:: :secnotoc:`Poznámky`

.. [#f1] Příklady Leaflet http://leafletjs.com/examples.html
.. [#f2] Dokumentace Leaflet http://leafletjs.com/reference.html
