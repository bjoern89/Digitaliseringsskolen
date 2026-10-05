# Digitaliseringsskolen

En læringsapp for ansatte i offentlig sektor som jobber med tjenesteutvikling, digitalisering, systemforvaltning, data og KI. Hver økt tar 3–5 minutter. Appen fungerer på PC, Android og iPhone og kan installeres på hjemskjermen.

## Appen (`docs/`)

- **Læringsløpet som linjekart:** fem linjer (deler) med 20 stasjoner (økter). Hver økt låses opp når du har fullført den forrige.
- **XP og nivåer:** sju nivåer fra «Nysgjerrig» til «Digitaliseringsmester».
- **Quiz:** tre spørsmål per økt med forklaring. Du får stjerner og bonus for feilfri quiz.
- **Streak:** teller hvor mange dager på rad du har lært noe.
- **Merker:** 13 merker for milepæler, blant annet ett per fullført linje og «Uteksaminert» for hele løpet.
- **Kursbevis:** vises på profilsiden når alle 20 øktene er fullført.
- **Refleksjonslogg:** svarene dine på refleksjonsspørsmålene samles på profilsiden.
- **Offline og installerbar:** PWA med manifest og service worker.

Fremgangen lagres lokalt i nettleseren (`localStorage`). Appen har ingen innlogging og sender ingen data til en server.

### Publisere med GitHub Pages

1. Gå til **Settings → Pages** i repoet.
2. Under *Build and deployment* velger du **Deploy from a branch**, deretter grenen og mappen **`/docs`**.
3. Appen blir tilgjengelig på `https://<bruker>.github.io/<repo>/`. Åpne lenken på mobilen og legg den til på hjemskjermen.

Du kan også teste lokalt med `npx serve docs` eller `python3 -m http.server -d docs`.

## Innhold

- **[Læringsplan](laeringsplan.md):** hele kompetanseløpet med alle 20 øktene.
- **[Agentinstruksjoner](agent-instruksjoner.md):** instruksen for læringsagenten og formatet for nye økter i appen.

Når du skal legge til en ny økt, ber du agenten lage den i appformatet og limer objektet inn i `LESSONS` i `docs/index.html`.
