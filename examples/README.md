# Exempel

Fristående flöden som hämtar data och skriver ut den i debug-fönstret. Inget av dem skickar DMX. På varje flöde finns en kommentar som visar var man kan koppla in en ljuscue.

| Fil | Vad den gör | Behöver |
| --- | --- | --- |
| `smhi-temp.json` | Hämtar senaste lufttemperaturen i Norrköping från SMHI var 60:e sekund. Värdet skrivs med decimalkomma. | Inget |
| `malarbron-broexempel.json` | Frågar Södertälje kommuns API var 30:e sekund om Mälarbron är öppen eller stängd. | Inget |
| `trafikverket-tagankomst.json` | Lyssnar på tågankomster via Trafikverkets SSE-ström och skriver ut varje tåg en gång. | Nodpaketet `@parasaurolophus/node-red-eventsource` och en API-nyckel |

## SMHI

Använder parameter 45 (lufttemperatur) och station 86340. Byt siffrorna i http-noden för en annan mätstation. Flödet visar också hur gammal mätningen är, eftersom SMHI inte uppdaterar stationen varje minut.

## Mälarbron

`state` är 1 när en broöppning pågår och 0 när bron är stängd. Kommentaren i flödet visar var en ljuscue kan startas.

## Trafikverket

Nyckeln och stationen läses från miljövariabler i Node-RED:

- `trafikverket_authkey`
- `trafikverket_station`

Lägg dem under Inställningar för flödet eller som miljövariabler där Node-RED startas. Skriv aldrig in nyckeln direkt i en nod om du ska dela flödet. Flödet håller reda på vilka tåg som redan visats och nollställer listan vid midnatt. Kommentaren efter noden för ankomster visar var DMX kan kopplas in.
