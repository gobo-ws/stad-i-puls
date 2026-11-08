# Flöden

Flöden som skickar DMX till belysningen via OLA (`POST http://localhost:9090/set_dmx`). De är gjorda för mina armaturer, så universum och kanaler behöver ändras för andra.

| Fil | Vad den gör | Status |
| --- | --- | --- |
| `parkering-linkoping-dukaten.json` | Summerar lediga platser i Linköpings parkeringshus från Dukatens API. Fler lediga platser ger en grön puls, färre en röd. | Ger just nu ingen puls, se nedan |
| `parkering-linkoping-old.json` | Samma idé mot Linköpings kommuns gamla API. | Fungerar inte längre |

## Parkering Linköping (Dukaten)

Flödet frågar `https://api.dukaten.parkknowit.com/api/parkings/external` var 120:e sekund, eftersom svaret cachas i upp till två minuter. Hela svaret är en lista med parkeringar. Det som används är `vehicleSpaces.total` och `vehicleSpaces.available`. Parkeringar utan platsräkning hoppas över.

Förändringen jämförs med föregående anrop. Ökar antalet lediga platser skickas en grön puls, minskar det en röd. Efter tre sekunder släcks kanalerna.

När jag skrev detta (november 2026) saknade svaret fältet `vehicleSpaces` helt, så flödet varnar i debug-fönstret och skickar ingen puls. Jag har frågat Dukaten och Linköpings kommun vart platsantalen tagit vägen. När svaret ändras behöver flödet inte ändras.

DMX-delen använder universum 4 och 30 kanaler. Ändra i funktionsnoderna "DMX grön puls" och "DMX röd puls".

## Parkering Linköping (gamla API:et)

Ligger kvar som exempel på hur det såg ut innan Linköping bytte till Dukaten. Flödet fungerar inte längre.
