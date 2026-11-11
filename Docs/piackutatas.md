# Piackutatás és Hasonló Alkalmazások

## 1. Bevezetés

A szakdolgozatom célja egy olyan asztali alkalmazás készítése Java Swing-ben, amellyel könnyen be lehet olvasni, szerkeszteni és vizualizálni adatbázis-sémákat. A fejlesztés előtt érdemes megnézni, hogy milyen hasonló programok léteznek már a piacon.

## 2. Hasonló alkalmazások

Íme néhány elterjedt eszköz, amelyek hasonló célt szolgálnak:

1. **DbSchema**
   * **Leírás:** Java alapú, vizuális adatbázis-tervező asztali program. Nagyon hasonló technológiát használ, mint a tervezett alkalmazásom.
   * **Link:** [https://www.dbschema.com/](https://www.dbschema.com/)

2. **MySQL Workbench**
   * **Leírás:** A MySQL hivatalos tervezőeszköze. Fő erőssége az ER-diagramok rajzolása és a séma-kezelés.
   * **Link:** [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/)

3. **DBeaver**
   * **Leírás:** Népszerű, nyílt forráskódú adatbázis-kezelő, amiben van egy beépített diagramnézet a sémák megjelenítésére.
   * **Link:** [https://dbeaver.io/](https://dbeaver.io/)

4. **dbdiagram.io**
   * **Leírás:** Webes alapú, gyors séma-tervező eszköz, ami szöveges leírásból rajzol diagramokat.
   * **Link:** [https://dbdiagram.io/](https://dbdiagram.io/)

5. **phpMyAdmin**
   * **Leírás:** Klasszikus, webes adatbázis-kezelő felület (PHP-alapú), ami tartalmaz egy alapvető vizuális tervező modult is.
   * **Link:** [https://www.phpmyadmin.net/](https://www.phpmyadmin.net/)

## 3. Összehasonlító táblázat

| Funkció / Tulajdonság | Saját Alkalmazás (Java Swing) | DbSchema | MySQL Workbench | DBeaver | dbdiagram.io | phpMyAdmin |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Környezet** | Asztali | Asztali | Asztali | Asztali | Webes | Webes |
| **Interaktív vizualizáció** | Igen | Igen | Igen | Igen | Igen | Alap szintű |
| **Séma beolvasás** | Egyedi parser | Igen | Igen | Élő adatbázis | DSL nyelv | Élő adatbázis |
| **Vektoros export (SVG)** | **Igen** | Igen | Igen | Korlátozott | Fizetős | Nem |
| **Offline működés** | **Igen** | Igen | Igen | Igen | Nem | Függ a szervertől |
| **Biztonsági validáció** | **Igen** | Alap | Alap | Alap | Nem releváns | Alap |

## 4. A Szerkesztők Működésének Technikai Finomságai

A piacon elérhető eszközök összehasonlításakor nem elégséges csupán a főbb funkciókat listázni; figyelembe kell venni az alábbi finomabb technikai részleteket is:
* **SQL szabvány támogatás és implementációk:** A különböző adatbázis-kezelők (pl. SQLite, PostgreSQL, MySQL) eltérően kezelik az SQL-dialektusokat és a típusegyezéseket. Saját alkalmazásom az SQLite fájlokra fókuszál, aminek sajátossága a dinamikus tipizálás (*Type Affinity*), míg más eszközök (pl. MySQL Workbench) szigorúbb relációs megkötéseket alkalmaznak.
* **Számosság megjelenítése:** A relációk (1:1, 1:N, N:M) vizuális jelölése (például *Crow's Foot* jelölésrendszer) komoly kihívást jelent összetettebb sémáknál a zsúfoltság elkerülése érdekében.
* **Automatikus táblaelrendezés:** A nagyméretű adatbázisok vizuális rendezése sok programban (például DBeaver automatikus nézeteiben) kaotikussá válhat, ezért a saját alkalmazásban kiemelt figyelmet kap a strukturáltabb megjelenítés.

## 5. Alternatív Eszközök és Szöveges Ábragenerátorok

Az adatbázis-sémák vizualizálására és dokumentálására nemcsak dedikált adatbázis-tervezők, hanem más kategóriájú eszközök is léteznek:
- **Általános diagramszerkesztők (draw.io, DIA):** Rugalmas, szabadkézi grafikai szerkesztést biztosítanak, de hiányzik belőlük az adatbázis-séma alapú automatikus validáció, a közvetlen fájlkezelés és a séma-export.
- **UML szerkesztők:** Kiválóak az objektumorientált szoftvertervezéshez, de a relációs adatbázisok fizikai sajátosságai (indexek, triggerek, adattípus-specifikumok) háttérbe szorulnak bennük.
- **Szöveges ábragenerátorok (PlantUML, Mermaid, TikZ):** 
  - *PlantUML / Mermaid:* Nagyon hatékonyak verziókezelés szempontjából (szöveges leírásból generálnak diagramot), de interaktív, egérműveletes vizuális szerkesztésre közvetlenül nem alkalmasak.
  - *TikZ:* Kiváló minőségű, professzionális LaTeX kimenetet ad, de a szerkesztési ideje túl magas egy dinamikus, interaktív tervezőhöz képest.

## 6. Összegzés

A fenti programok nagyrészt nehezebb, komplex adatbázis-kezelők vagy webes szolgáltatások. Az én alkalmazásom egy könnyen használható, önálló asztali eszköz lesz, ami egyedi elemzéssel, biztonsági szűréssel és SVG/PNG exporttal segíti a munkát.