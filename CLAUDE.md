# Yatzy – Hinweise für Claude

Würfelspiel für Ronny und Familie. Live: https://rschieler.github.io/Yatzy/ (GitHub Pages, Branch `main`, Root).

## Grundsätze
- Schweizer Schreibweise («ss», Anführungszeichen « »). Ronny will knappe Antworten und fertige Lösungen statt Optionen, auf Deutsch.
- Alles in **einer Datei `index.html`**, keine Build-Schritte. Nach Änderungen an eigenen Dateien in `sw.js` die Cache-Version `C` erhöhen.

## Regeln (Hausregeln, nicht ändern ohne Auftrag)
- Oben Einer–Sechser, Bonus **25** ab 63.
- Ein Paar / Zwei Paare / 3x / 4x: Summe nur der gleichen Würfel. Kleine Strasse = 4 in Folge (20), grosse = 5 in Folge (30), Full House immer 25, Chance = Summe, Yatzy 50. Max. 361.
- Reihenfolge unten: 2x, 2x2, 3x, 4x, kl. Strasse, gr. Strasse, Haus, Chance, Yatzy.

## Aufbau
- `CATS` Kategorien, `score()` Punkte, `bonus()`, `total()`.
- Bot: `buildV0`/`buildV1`/`bestHold` (Halte-Entscheide über alle 252 Würfelzustände, Bewertung `val()` mit `PAR`), `botTurn()` spielt sichtbar, startet 1,6 s nach dem Setzen des Spielers.
- Feld antippen wählt (`sel`), Knopf «Setzen» trägt ein. Rückgängig (`undo`) bis zum nächsten eigenen Wurf, setzt auch den Bot-Zug zurück.
- Würfel: 3D-Würfel (`.cube`, `setCube`, `ORI`, `animateRoll`), Klang per Web Audio (`tick`, `knock`), Vibration.
- Menü: Neues Spiel (Bot/Solo/Mehrspieler 2–4), Bestenliste, Farbdesign (`SKINS`, CSS `[data-skin]`), Würfelgeräusch, Schütteln zum Würfeln (`devicemotion`), Einhandmodus (`body.one`, Vorschläge `renderChips`), Spielregeln.
- localStorage-Schlüssel `yatzy2.*` (game, best, bot, setup, skin, snd, shake, one).
