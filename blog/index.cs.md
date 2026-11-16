# Protocol Tracer: stromový přehled hodnot zařízení

**Protocol Tracer (TracerUI)** je desktopová aplikace v C++ a Qt pro cyklické čtení a řízení nakonfigurovaných hodnot zařízení. Komunikační úlohy, oblasti a typované uzly zobrazuje v editovatelném stromu. Podle protokolu a XML konfigurace podporuje Modbus, OMC8000 a ELM327.

![Rozhraní Protocol Traceru se stromem nakonfigurovaných hodnot a údaji o čtení a zápisu](../screenshots/Tracer01.png)

## Přehled v reálném čase

Po načtení XML profilu aplikace zobrazí úlohy a jejich datové oblasti. V tabulce lze sledovat přečtené a zapisované hodnoty, časy čtení a zápisu, popisy a stavové indikátory. Konfigurované úlohy lze spustit a zastavit z panelu nástrojů; zapisovatelné uzly lze upravit ve sloupci **W**.

Nejde o univerzální zachytávač surových paketů. Aplikace cyklicky pracuje s hodnotami a uzly definovanými v profilu a zobrazuje související stav a chyby.

## Podporované profily

- **Modbus** – sériové nebo ethernetové úlohy a oblasti s typem, adresou, počtem a přístupem pro čtení či zápis.
- **OMC8000** – úlohy přes sériové nebo síťové rozhraní.
- **ELM327** – sériové úlohy pro práci s uzly definovanými v profilu.

Konfigurace popisuje úlohy, oblasti a uzly. Úloha obsahuje spojení a periodu cyklu; oblast určuje datový typ a přístup; uzel definuje typovanou hodnotu, offset a popis. Aplikace z kořenového XML elementu (`modbus`, `omc8000` nebo `elm327`) zvolí odpovídající model.

## Spuštění

V repozitáři je 64bitová sestava pro Windows v `bin/msvc2017_64/`. Spusťte `TracerUI.exe`, otevřete odpovídající XML profil přes **File → Open** a před spuštěním úloh upravte komunikační parametry a adresy pro konkrétní testovací prostředí.

Zdrojový projekt používá Qt 5 a qmake. Pro sestavení 64bitové varianty otevřete `TracerUI_64.pro` v Qt Creator s Qt 5.14.2 a MSVC 2017 64bitovým kitem. Popis formátu konfigurace je v [`TracerUI.txt`](../TracerUI.txt).

> **Upozornění:** Zápis ve sloupci **W** může měnit hodnoty na připojeném zařízení. Před spuštěním ověřte mapování adres, přístupová práva i cílové testovací zařízení.

Zdrojový kód: [CodElecCz/protocol-tracer](https://github.com/CodElecCz/protocol-tracer).
