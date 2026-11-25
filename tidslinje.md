# Tidslinje: rita vad som händer

Välj snutt 5 och snutt 10. Fyll i tabellerna steg för steg. Skriv vad som ligger i varje del **efter** varje steg.

Förklaring:

- **Anropsstacken** är den kod som körs just nu.
- **Microtask-kön** är promise-callbacks som väntar på att få köra.
- **Task-kön** är timer-callbacks och liknande som väntar på att få köra.
- Regel: när stacken är tom körs först ALLA microtasks, sedan EN task, sedan tomma microtasks igen, och så vidare.

## Snutt 5

| Steg | Vad händer                          | Stacken                      | Microtask-kön                            | Task-kön | Utskrift hittills |
| ---- | ----------------------------------- | ---------------------------- | ---------------------------------------- | -------- | ----------------- |
| 1    | setTimeout anropas                  | setTimeout                   | tom                                      |          |                   |
| 2    | Promise.resolve().then(...) anropas | .then                        | console.log("promise")                   |          |                   |
| 3    | console.log("sync")                 | console.log("sync")          | Stacken tom: vad körs först? (Microtask) |          |                   |
| 4    | Stacken tom: vad körs först?        | console.log("promise")       |                                          |          |                   |
| 5    | Nästa                               | () => console.log("timeout") |
|      |                                     |                              |

## Snutt 10

| Steg                   | Vad händer                | Stacken                                        | Microtask-kön          | Task-kön | Utskrift hittills    |
| ---------------------- | ------------------------- | ---------------------------------------------- | ---------------------- | -------- | -------------------- |
| 1                      | console.log("1")          | console.log("1")                               |                        |          |                      |
| 2                      | första setTimeout         | 1a settimeout                                  |                        |          | kö: () => console.lo |
|                        |
| 3                      | Promise.resolve().then(3) | Promise.resolve.then(3)                        | () => console.log("3") |          | kö () => console.lo  |
| 4                      | andra setTimeout          | andra setTimeout                               |
| () => console.log("3") |                           | kö 4 () => console.log("2"), () => { log("4"); |

|
| 5 | console.log("6") | console.log("6") | () => console.log("3")| | kö () => console.log("2"), () => { log("4"); ...|
| 6 | stacken tom, microtask-kön först | stacken tom | | | kö 6
() => console.log("2"), () => { log("4"); ..
|
| 7 | första tasken | 1a tasken | | | kö
() => { log("4"); ... }
|
| 8 | andra tasken | 2a tasken |() => console.log("5") | | |
| 9 | microtask 5 |microtask 5 | | | |

## Min förklaring i en mening

Varför kommer en promise-callback före en timer med 0 ms?
promise har högre prio än task
