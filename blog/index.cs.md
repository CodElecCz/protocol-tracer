# Protocol Tracer: diagnostika a monitoring průmyslových protokolů

**Protocol Tracer (TracerUI)** je desktopová aplikace napsaná v C++ s využitím Qt 5.14.2. Slouží k cyklickému monitorování a řízení hodnot zařízení. Komunikační úlohy, datové oblasti a jednotlivé proměnné přehledně zobrazuje v editovatelném stromu. Podporuje protokoly Modbus, OMC8000 a ELM327; nastavení se načítá z XML profilů.

![Rozhraní Protocol Traceru se stromem nakonfigurovaných hodnot a údaji o čtení a zápisu](../screenshots/Tracer01.png)

## Monitorování hodnot v reálném čase

Po načtení XML profilu aplikace zobrazí jednotlivé úlohy a jejich datové oblasti. V tabulce jsou k dispozici načtené a zapisované hodnoty, časy čtení a zápisu, popisy i stavové indikátory. Úlohy lze spouštět a zastavovat z panelu nástrojů. Hodnoty, které profil dovoluje zapisovat, se upravují ve sloupci **W**.

Protocol Tracer není určen k pasivnímu odposlechu (snifferu) surových paketů. Cyklicky čte a zobrazuje proměnné definované v profilu a informuje o jejich stavu a případných chybách komunikace.

## Podporované protokoly a profily

- **Modbus** – komunikace po sériové lince nebo Ethernetu; oblasti určují typ, adresu, počet hodnot a oprávnění ke čtení či zápisu.
- **OMC8000** – komunikace přes sériové nebo síťové rozhraní.
- **ELM327** – sériová komunikace s proměnnými definovanými v profilu.

XML profil popisuje úlohy, datové oblasti a jednotlivé proměnné. U každé úlohy se nastavuje spojení a perioda cyklu, oblast určuje datový typ a přístupová práva a proměnná obsahuje typ, offset a popis. Aplikace podle kořenového XML elementu (`modbus`, `omc8000` nebo `elm327`) vybere příslušný model.

## Spuštění

V adresáři `bin/msvc2017_64/` je připravena 64bitová sestava pro Windows. Spusťte `TracerUI.exe` a načtěte vhodný XML profil pomocí **File → Open**. Před spuštěním úloh zkontrolujte a upravte komunikační parametry i adresy podle testovacího prostředí.

Projekt se sestavuje pomocí qmake. Pro 64bitovou variantu otevřete `TracerUI_64.pro` v Qt Creator a zvolte 64bitový MSVC 2017 kit s Qt 5.14.2. Formát XML konfigurace podrobněji popisuje soubor [`TracerUI.txt`](../TracerUI.txt).

> **⚠️ Bezpečnostní upozornění:** Zápisem ve sloupci **W** lze změnit hodnoty připojeného zařízení. Před spuštěním ověřte správnost mapování adres a přístupových práv a ujistěte se, že pracujete s určeným testovacím zařízením.

Zdrojový kód: [CodElecCz/protocol-tracer](https://github.com/CodElecCz/protocol-tracer).
