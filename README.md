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

Løpet har 20 økter fordelt på fem linjer:

1. **Grunnmuren:** KI-agenter, språkmodeller, automatisering, Power Platform og Copilot Studio (økt 1–5)
2. **Data som fundament:** datakvalitet, informasjonsforvaltning, dataforvaltning, Microsoft Fabric og RAG (økt 6–10)
3. **Trygg og ansvarlig bruk:** personvern, cybersikkerhet og KI-forordningen (økt 11–13)
4. **Fra idé til tjeneste:** sammenhengende tjenester, produktorientering, tjenestedesign og arkitektur (økt 14–17)
5. **Effekt og endring:** gevinstrealisering, endringsledelse og den agentiske organisasjonen (økt 18–20)

Faktapåstandene er kontrollert mot kildene i [kilder.md](kilder.md).

### Legge til eller endre en økt

Øktene ligger i listen `LESSONS` i `docs/index.html`. Hver økt er et objekt i dette formatet:

```js
{
  id: 21, part: 5, min: 4, title: "Tittel",
  intro: "Kort introduksjon med kobling til forrige økt.",
  explain: `<p>Forklart på 1 minutt (enkel HTML: p, ul, ol, strong).</p><p class="keyline">Én setning å huske.</p>`,
  why: ["<strong>Poeng.</strong> Forklaring.", "..."],          // 3–5 punkter
  example: `<p>Realistisk eksempel fra offentlig sektor.</p>`,
  reflect: "Ett refleksjonsspørsmål om egen organisasjon.",
  next: "Én setning om neste tema.",
  quiz: [                                                       // nøyaktig 3 spørsmål
    { q: "Spørsmål?", a: ["Alt A", "Alt B", "Alt C", "Alt D"], c: 1, x: "Kort forklaring av riktig svar." }
  ]
}
```

`part` er linjenummeret (1–5), og `c` er indeksen til riktig svar, der 0 er det første alternativet. Øktene låses opp i rekkefølge etter `id`, så nye økter må få fortløpende nummer. Øk versjonsnummeret i `CACHE` i `docs/sw.js` når du endrer innhold, slik at installerte apper henter den nye versjonen.

## Lisens

- **Kildekoden** er lisensiert under [MIT-lisensen](LICENSE).
- **Læringsinnholdet** (øktene, quizene og eksemplene) er lisensiert under [Creative Commons Navngivelse 4.0 Internasjonal (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.no). Du kan dele og tilpasse innholdet, også kommersielt, så lenge du oppgir Digitaliseringsskolen som kilde og angir om du har gjort endringer.
