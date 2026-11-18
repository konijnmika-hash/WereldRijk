# Wereldrijk

Strategiespel in de browser: verover de wereld, alleen, samen op één telefoon of online met vrienden.

**Spelen:** open `index.html`, of de GitHub Pages-site van deze repository.

## Wat zit erin
- Een kalender: je begint op 1 januari 2026 en elke beurt is één maand; in de winter is oorlog in koude landen zwaarder
- Een leger dat bij je bevolking past: werving per maand, maximale legergrootte, tankbemanning en piloten hangen af van je inwoners; wapens zijn duur en kosten onderhoud
- Mobilisatie: in 2026 groeien alle legers (ook van de computer) nog langzaam
- Onderzoek: drones, precisiebommen, luchtafweer, kruisraketten, bunkerbrekers, stealthbommenwerpers, EMP-raketten, hypersone raketten en de waterstofbom
- Vertrouwen: wie een bondgenoot of handelspartner aanvalt, wordt door de hele wereld minder vertrouwd
- Tik op een land om te zien met wie het samenwerkt en met wie het in oorlog is; echte bondgenootschappen en handelsverdragen bij de start
- Nieuws onder kopjes: samenvoegingen en verbonden, oorlog, veroverd land, vrede en diplomatie
- Echte landen, een front dat over de hele grens opschuift, terrein, moreel en oorlogsmoeheid
- Legers per continent, met op de kaart bij elk continent hoeveel soldaten en tanks er staan
- Kernwapens: Kernprogramma, Raketschild, doelwit kiezen op de kaart, radioactieve neerslag en kernmachten die terugslaan
- Onrust: veroverd land moet wennen en kan in opstand komen; laat troepen achter of handhaaf de orde
- Gebeurtenissen met keuzes, doelen met beloningen en spionage (sabotage, opstand stoken, technologie stelen)
- Diplomatie, coalities, overgave en samengaan van landen
- Geluidseffecten (aan/uit in het menu)

## Tijdperken
In het menu kies je bij **Tijdperk** waar je begint: in 2026 of in een van 15 oorlogen, steeds op het hoogtepunt:
Slag bij Kadesh (1274 v.Chr.), Grieks-Perzische oorlogen (480 v.Chr.), Peloponnesische Oorlog (431 v.Chr.), Punische oorlogen (218 v.Chr.),
Verovering van Gallië (58 v.Chr.), Byzantijns-Perzische oorlog (622), Arabische veroveringen (732), Kruistochten (1140), Mongoolse veroveringen (1279),
Honderdjarige Oorlog (1429), Dertigjarige Oorlog (1629), Zevenjarige Oorlog (1756), Napoleontische oorlogen (1812), Eerste Wereldoorlog (1918) en Tweede Wereldoorlog (1942).

- Elk tijdperk heeft de landen, namen en grenzen van toen (bezet gebied hoort bij de bezetter, dus bijvoorbeeld het grootste Duitsland in 1942), met de bondgenootschappen en oorlogen van die maand
- Je speelt elk land met zijn echte leger en economie; de kalender loopt vanaf die maand verder
- Wapens passen bij de tijd: strijdwagens, ruiters, olifanten, ridders, katapulten, kanonnen, Grieks vuur; tanks en vliegtuigen pas in de wereldoorlogen
- Een tijdperk is ook te openen met `index.html?tijd=ww2` (ids: kadesh, perzen, pelop, punisch, gallie, byzperz, arabisch, kruis, mongolen, honderd, dertig, zeven, napoleon, ww1, ww2)
- De kaarten staan in `eras/`; ze worden gemaakt met de scripts in `tools/eras/` uit de historische grenzen van
  [historical-basemaps](https://github.com/aourednik/historical-basemaps) plus eigen correcties per oorlog (`tools/eras/prepare.sh`, daarna `./build_all.sh`)

## Online spelen
Online spelen loopt via gratis openbare MQTT-servers (EMQX, HiveMQ, Mosquitto), die over WebSocket bereikt worden.
Een account is niet nodig. De spelstatus wordt als "retained" bericht opgeslagen, zodat je na het verversen
van de pagina met dezelfde code weer kunt meedoen. De pagina verbindt met alle servers tegelijk en gebruikt
steeds de nieuwste versie, dus het spel blijft werken als één server uitvalt.

Een eigen broker gebruiken: `index.html?broker=wss://jouw-server:poort/mqtt`.

Let op: dit zijn openbare servers. Iedereen die de spelcode kent, kan meekijken.

## Bestanden
- `index.html`: het spel
- `net.js`: online-laag (kleine documentdatabase op MQTT)
- `vendor/mqtt.min.js`: MQTT.js 5.16.1 (MIT)
- `eras/*.js`: de kaarten en landen per tijdperk
- `tools/eras/`: scripts om de tijdperken opnieuw te bouwen
