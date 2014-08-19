OpenLayers a WFS-T
==================

.. note:: Nastavení editace vektorových dat pomocí protokolu WFS-T vyžaduje již
    určité programátorské schopnosti. Tento příklad berte pouze jako
    ilustrativní, pro reálný systém je potřeba ošetřit celou řadu krajních
    případů. Příklad vychází z oficiální dokumentace k TinyOWS [#f4]_.

.. raw:: html

    <iframe src="../_static/web/openlayers-wfst.html" width="620" height="420"></iframe>

Editace pomocí protokolu WFS-T (transakční WFS) vyžaduje jednak
nastavení na straně serveru a jednak přidání editačních nástrojů do
projektu OpenLayers.  Pokračovat budeme na `předchozím příkladě
<../_static/web/openlayers.html>`_, ale poněkud jej rozšíříme. Verzi s
WFS-T si můžete prohlédnout `zde
<../_static/web/openlayers-wfst.html>`_.

Nejprve přidáme do seznamu strategií u vrstvy WFS strategii pro ukládání:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 131,136-148
   :emphasize-lines: 131,137

Přidáme nástroje pro kreslení nových prvků a změnu existujících prvků v mapě:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 154-157,163-171,178-180,193-195

Nakonec vyrobíme tlačítko s ukládací funkcí:

.. literalinclude:: ../_static/web/openlayers-wfst.html
   :language: javascript
   :lines: 182-192

Závěr
-----
Tento příklad je (už při pohledu na zdrojový kód) poměrně komplexní - v úvodu
souboru jsme museli nastavit kaskádové styly jednotlivých tlačítek, museli jsme
definovat funkce pro mazání prvků a pro odeslání prvků protokolem WFS-T na
server, přidávat tlačítka pro editaci geometrií ručně v kódu. 

OpenLayers je poměrně komplexní knihovna - na úrovni jiných programátorských
knihoven používaných v GIS. S její pomocí lze vytvořit velice funkční aplikace,
ale jen velice málo funkcí je *hotových k okamžitému použití* pro
laika-neprogramátora.

Další věc, která v příkladu není nijak ošetřena, je autorizace a autentifikace
uživatele. Předpokládáme čtení/zápis pro všechny. Obecně je toto na webu
problém, mapová aplikace musí být dostupná ze stejné URL jako WFS server -
tak, aby nedocházelo k problémům s tzv. *cross site scripting*. V tom případě
totiž není jednoduše možné předat přihlašovací údaje vzdálenému serveru, neboť
jsou zachyceny právě na službě proxy.

.. rubric:: :secnotoc:`Poznámky`

.. [#f4] Příklad pro TinyOWS a OpenLayers http://mapserver.org/tinyows/openlayershowto.html
