# Adatbázis-séma elemző és vizualizáló asztali alkalmazás

Szakdolgozat projekt a Miskolci Egyetem Gépészmérnöki és Informatikai Kar Programtervező informatikus BSc képzésén.

## A dolgozat címe és témája
- **Cím:** Relációs séma és diagram szerkesztő alkalmazás fejlesztése
- **Konzulens:** Dr. Tompa Tamás
- **Szakmai konzulens / Architektúra tanácsadó:** Piller Imre, Dr. Tompa Tamás

## Feladatleírás
A szakdolgozat célja egy olyan asztali grafikus felhasználói felülettel (GUI) rendelkező alkalmazás fejlesztése Java nyelven (Swing keretrendszer és FlatLaf megjelenés használatával), amely képes statikus SQL (DDL) adatbázis-sémák beolvasására, elemzésére, valamint az adatbázis-szerkezetek (táblák, attribútumok, idegen kulcs kapcsolatok) interaktív, testreszabható grafikus vizualizációjára.

A szoftver kiemelt figyelmet fordít a bemeneti fájlok biztonsági validációjára (nem DDL jellegű vagy kártékony SQL utasítások előszűrése) és a rugalmas exportálási lehetőségekre (PNG és SVG vektoros formátumok), hogy a generált diagramok közvetlenül beilleszthetők legyenek dokumentációkba vagy prezentációkba.

## Projekt struktúra
- `Docs/` – Rendszertervek, felületi specifikáció (`felulet.md`), piackutatás (`piackutatas.md`) és a hozzájuk tartozó ábrák (`Images/`)
- `Szakdolgozat/` – A szakdolgozat szöveges dokumentuma és forrásai
- `Editor/` – A Java Swing alapú szerkesztő és SQL parser forráskódjai
- `README.md` – Projekt áttekintés és dokumentáció

## Technológiai stack
- **Nyelv:** Java
- **UI keretrendszer:** Java Swing (FlatLaf)
- **Adatbázis & SQL:** Statikus SQL DDL sémák (`CREATE TABLE`, `PK`/`FK` megkötések)
- **Verziókövetés:** Git, GitHub
- **Dokumentáció:** Markdown, draw.io, LaTeX

## Főbb funkciók és tervezett modulok
1. **Séma-elemzés (Parser):** Statikus `.sql` sémafájlok lexikális és szintaktikai feldolgozása, táblák, mezők és relációk kinyerése.
2. **Biztonsági validáció:** Beépített előszűrés és input-ellenőrzés a tiltott vagy kártékony SQL utasítások kiszűrésére.
3. **Grafikus vizualizáció:** Az adatbázis-objektumok interaktív megjelenítése `Graphics2D` vásznon, szabad mozgatással (*drag-and-drop*), nagyítással (zoom) és eltolással (pan).
4. **Exportálási lehetőségek:** A szerkesztett diagramok mentése raszteres (**PNG**) és skálázható vektoros (**SVG**) formátumban.