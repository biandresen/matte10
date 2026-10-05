# Matematikk 10 – nettstedsspesifikasjon

## Formål og innhold

Et oversiktlig nettsted for elever på 10. trinn som trenger enkle forklaringer, små steg og tydelig progresjon. All HTML i dette repositoryet er offentlig elevinnhold. Ingen lærermerknader, poengrubrikker, elevdata eller ufrigitte fasiter skal ligge her, heller ikke skjult eller uten lenker.

## Struktur og stabile adresser

- `index.html`: forside med toppfelt og elevillustrasjon. Begreper er alltid første innholdskort rett under toppfeltet, deretter hovedtemaer og tidligere ressurser.
- `begreper/index.html`: én felles begrepsbank for hele året.
- `<hovedtema>/index.html`: oversikt over undertemaer.
- `<hovedtema>/<nummer-slug>/leksjon.html`: forklaring med eksempler.
- `<hovedtema>/<nummer-slug>/index.html`: samling av frigitte ressurser.
- `ovingsoppgaver/oppgaver.pdf`, `prove/prove.pdf`, `fasit/oving.html` og `fasit/prove.html` under undertemaet publiseres bare når de frigis.
- Tidligere prøvefasit ligger i `algebra/tidligere-prover/uke-38-2026/index.html`. Bevar gamle fragment-ID-er og eksisterende omdirigering fra gamle forsidebokmerker.

Bruk små ASCII-bokstaver og bindestrek i URL-er. Bruk norsk bokmål i synlig tekst. GitHub Pages bruker `main` og `/`, med `.nojekyll`. Ingen byggtjeneste, eksterne fonter eller nettavhengige skript er nødvendige.

## Obligatorisk navigasjon

1. **Hjem:** synlig lenke i toppfeltet, til nettstedets `index.html`. Den må fungere også etter flere interne sidebytter i fokusmodus.
2. **Brødsmuler:** på alle sider unntatt forsiden. Vis nettstedshierarkiet, ikke besøkshistorikken. Eksempel: Hjem / Algebra / Faktorisering / Øvingsoppgaver med fasit. Siste element har `aria-current="page"` og er ikke en lenke. Bruk `nav` med `aria-label="Brødsmuler"` og en ordnet liste. Ikke lenk til en undertemaoversikt som ennå ikke er frigitt.
3. **Innholdsmeny:** alle sider under et hovedtema får lenker til sidens hovedavsnitt (h2), pluss Begreper. På PC ligger menyen til venstre og følger rullingen. På mobil vises den som «På denne siden» over innholdet og kan åpnes/lukkes. Menyen må ikke dekke teksten. Bruk stabile, unike fragment-ID-er og synlig tastaturfokus.
4. **Ingen Tilbake/Fremover-historikknapper i toppfeltet.** Hjem og brødsmuler brukes til stedsnavigasjon. Nettleserens egen historikk skal fortsatt fungere. Lenker mellom deler av samme prøve er innholdslenker og kan beholdes.
5. Ressursknapper som «Øvingsoppgaver · PDF» beholdes der de hjelper eleven videre. Unngå en ekstra konkurrerende rad med gamle «til oversikt»-lenker over brødsmulene.

## Fokusmodus

Bevar tydelig turkis fullskjermknapp og eksplisitt avslutning. Bakgrunnsdekor skjules i fokusmodus. Ved intern navigasjon beholdes det ytre dokumentet; innholdet lastes i en intern iframe. Rammen skal ikke opprette en ny ramme eller vise et ekstra toppfelt inni seg. URL, sidetittel og nettleserhistorikk oppdateres. Hjem og brødsmuler må bruke samme navigasjon slik at fullskjerm beholdes.

Fullskjerm startes bare etter et klikk. Full omlasting eller ny fane krever et nytt klikk. Ved avvist eller manglende fullskjermstøtte tilbys roligere visning uten å hevde at nettleseren er i fullskjerm. Ingen automatisk aktivering, tastaturlås eller personsporing.

## Begrepsbanken

Én felles oversikt som vokser gjennom året. Startinnholdet har grunnbegreper, potenser, brøk, algebra/parenteser og geometri. Ikke opprett en konkurrerende ordliste for hvert nytt hovedtema.

Hver oppføring har en stabil ID, navn, gruppe, kort elevvennlig forklaring og et riktig eksempel. Bruk åpnefelt for forklaring/eksempel og et tydelig merket søk som filtrerer navn og innhold. Vis antall treff og beskjed ved null treff. Alt skal kunne leses uten JavaScript. Direkte lenker som `begreper/index.html#faktorisering` åpner riktig begrep. Ved nytt tema: gjenbruk eksisterende ord, legg til nødvendige nye begreper og forklar eventuelle nevner-/gyldighetsvilkår.

## Visuell stil og tilgjengelighet

Mørk blå bakgrunn med diskrete SVG-motiver, lyse lesekort, mørk tekst. Vanlige knapper har lys blå bakgrunn `#dcecfb`, mørk tekst `#173e60` og mørkere hover `#bfdcf4`. Temaoversikter med frigitte fasiter bruker alltid `class="pill pill-primary"`: mørkere blå `#285a82`, hvit tekst, hover `#1c4669` og en diskret blå glød. Dette gir oversiktsknappen høyere visuell vekt enn den lyse «Forklaring og eksempler»-knappen. Gjenbruk klassen for tilsvarende oversiktsknapper når nye undertemaer frigis. Gløden er statisk, uten pulsering. Fullskjermknappen bruker turkis. En liten SVG med fem elever vises bare på forsiden.

Bruk semantisk HTML, ett h1, logiske h2/h3, `<details>/<summary>`, synlig fokus, norsk dokument-språk og viewport. Ingen animasjon eller flashing som konkurrerer med fagstoffet. Sideinnholdet skal fungere uten eksterne bilder, skrifter eller JavaScript-biblioteker. Skjul navigasjon og dekor ved utskrift. PDF-ark skal fortsatt være oversiktlige A4-ark med plass til utregning.

## Kilder og videre arbeid

Det offentlige repoet inneholder ferdige HTML/PDF-ressurser. I det tilknyttede arbeidsmiljøet bygges algebra med `verktøy/algebra/bygg.py`. Felles moduler er `nettema.py` (stil), `fokus.py` (fullskjerm), `navigasjon.py` (Hjem/brødsmuler/innholdsmeny), `elever.py` (SVG) og `begreper.py` (begrepsdata). Frigivelse styres av `publisering.json`. Spesifikasjonen og AGENTS.md har kilder under `verktøy/algebra/nettsted-spec/`.

Hvis disse kildene er tilgjengelige: endre dem, bygg og kontroller resultatet. Hvis en ny chat bare har matte10: bruk de eksisterende sidene som mal og følg denne spesifikasjonen; ikke anta tilgang til andre repoer. Ikke publiser generatorens private innhold. Utvid generatoren før nye hovedtemaer tas inn, slik at den ikke senere overskriver nye sider eller begreper.

## Kontroll før publisering

- Alle lokale lenker og fragmenter virker; ingen lenker går til ufrigitte filer.
- Hjem og brødsmuler er riktige på hvert nivå. Forsiden har ikke brødsmuler.
- Innholdsmenyen virker på PC og mobil uten vannrett overflyt.
- Fokusmodus beholdes fra forside til undertema, leksjon, fasit, Begreper og Hjem. Ingen nestede innholdsrammer.
- Søket i Begreper virker med treff, null treff og tømming; direkte begrepslenker åpner riktig oppføring.
- Lærerstoff er fraværende også i HTML-kilden. Dokumentasjonen skal ikke lenkes fra elevsidene.
- Kontroller ferdig GitHub Pages-bygg og sidene på nett før endringen beskrives som publisert.
