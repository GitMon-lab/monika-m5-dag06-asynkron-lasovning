# Förutsägelser: asynkron kod

Regler:

1. Titta på snutten i `snuttar/sNN.js` (eller på sidan `index.html`). **Kör den inte än.**

2. Skriv din gissning i tabellen: utskrifterna i den ordning du tror att de kommer, separerade med `|`.

3. Kör snutten (knappen _Kör_). Skriv vad som faktiskt skrevs ut.

4. Hade du rätt? Skriv en regel med egna ord för varje snutt du gissade fel på.

| Snutt | Min gissning (i ordning) | Faktisk utskrift     | Rätt? | Min regel om jag hade fel |
| ----- | ------------------------ | -------------------- | ----- | ------------------------- |
| 1     | 1 2 3                    | 1 2 3                |       |
| 2     | A C B                    | A C B                |       |
| 3     | noll kort 300            | start noll kort lång |       | Missade start             |
| 4     |

const p = new Promise((resolve) => { //konstruktor körs först inuti promise efter then klart Allt körsinte klart
console.log("inuti promise");
resolve("klart"); //Promise
});
p.then((v) => console.log("then:", v)); //.then läggs på kö
console.log("efter"); // när allt är klar körs detta

| | inuti promise klart then efter | inuti promise efter then:klart | Nej | Konstruktor först . Allt inom new Promise körs direkt körs. Allt ionom .then() körs sist

| 5 |sync promis | sync promis timeout | delvis | |

| 6 | först? 6 7 |först? 6 7 | | synkron först sedan then|
| 7 | slut på mjölk fel städer| fel: slut på mjölk städar| | felet först, eftersom det är fel går den till catch fel |
| 8 | beställer sätter mig bullen klar kaffet klar|beställer sätter mig bullen klar kaffet klar | | |
| 9 | väntar på båda bulle kaffe |väntar på båda ["kaffe","bulle"] | | missade array|
| 10 | | | | |
| 11 | | | | |

## Tre meningar med egna ord

1. JavaScript väntar inte på `setTimeout`, utan ...lägger lägger funktioner på kö

2. En promise har tre tillstånd: ... pending(väntar på resultat) fulfilled(klart) rejected (fel/avvisat)

3. `then` körs alltid ... asynkront(på linje) dvs efter all vanlig synkron kod (på rad) körts klart ochnär promise är klart
