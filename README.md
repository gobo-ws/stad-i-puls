# Stad i puls

Ett ljuskonstverk i Norrköping där stadens egna data styr ljuset. Tågtrafik, parkering, väder och broöppningar hämtas från öppna API:er i Node-RED och blir DMX-signaler till belysningen.

Projektet är ett stipendieprojekt från Bertil & Britt Svenssons stiftelse för belysningsteknik. Av Johan Nilsson, [gobo.ws](https://gobo.ws).

## Innehåll

- [`examples/`](examples) har fristående exempel som hämtar data från ett API och visar resultatet i debug-fönstret. De fungerar utan DMX och utan någon ljusutrustning.
- [`flows/`](flows) har de flöden som körs i själva verket och som skickar DMX via OLA.

Varje mapp har en egen README som beskriver flödena.

## Så använder du ett flöde

1. Öppna Node-RED.
2. Välj Meny, Importera, och klistra in innehållet i en JSON-fil eller välj filen.
3. Läs kommentaren på fliken (fliken Info) och kontrollera vilka inställningar flödet behöver.
4. Tryck på Deploy.

## Det du behöver

- [Node-RED](https://nodered.org)
- För exemplet med tåg: nodpaketet `@parasaurolophus/node-red-eventsource` och en egen API-nyckel från [Trafikverket](https://data.trafikverket.se).
- För DMX-flödena: [OLA (Open Lighting Architecture)](https://openlighting.org/ola/) som körs på samma dator, med HTTP-servern på port 9090.

## Status

Parkeringsflödet för Linköping är byggt men får just nu inga platsantal från Dukatens API. Se [flows/README.md](flows/README.md).

## Licens

MIT, se [LICENSE](LICENSE).
