# Linse-katalog

Vælg 3–5 linser pr. opgave. Hver linse har et fokus, kernespørgsmål og en klar grænse ("ikke"), så linserne holdes MECE.

| Linse | Fokus | Kernespørgsmål | Ikke |
|---|---|---|---|
| **Økonomi** | Omkostninger, indtægter, cash flow, investering, ROI | Hvad koster det, hvad giver det, hvornår, og hvor følsomt er tallet? | Organisatoriske konsekvenser |
| **Governance** | Beslutningsret, ansvar, compliance, regulering, kontrakter | Hvem må beslutte, hvem bærer ansvaret, hvilke regler binder? | Teknisk gennemførlighed |
| **Data & evidens** | Kildegrundlag, datakvalitet, målbarhed | Hvad ved vi faktisk, og hvad er antagelser? Kan effekten måles? | Selve anbefalingen |
| **Risiko** | Nedside, usikkerhed, afhængigheder, reversibilitet | Hvad kan gå galt, hvor sandsynligt, hvor alvorligt, og kan det rulles tilbage? | Opside og gevinster |
| **Kunde / bruger** | Dem der mærker ændringen udefra | Hvad ændrer sig for kunden/borgeren/brugeren, og hvad vil de gøre? | Intern drift |
| **Drift & implementering** | Processer, systemer, kapacitet, tidsplan | Kan vi gøre det med de folk, systemer og den tid vi har? Hvad er kritisk vej? | Om vi bør |
| **Mennesker & forandring** | Medarbejdere, kompetencer, kultur, modstand | Hvem taber, hvem vinder, hvad skal folk kunne, hvor kommer modstanden fra? | Kunden |
| **Strategi & marked** | Position, konkurrenter, alternativer, langsigtet retning | Styrker det vores position? Hvad gør alternativerne/konkurrenterne? | Detaljeret økonomi |
| **Teknologi & arkitektur** | Systemlandskab, integration, sikkerhed, teknisk gæld | Passer det ind, hvad skal bygges/købes, hvilke sikkerhedskrav? | Forretningscase |

## Standardsæt
- **Beslutning om at gøre / ikke gøre noget:** Økonomi, Risiko, Drift & implementering, Kunde/bruger.
- **Organisations-/procesændring:** Governance, Mennesker & forandring, Drift & implementering, Data & evidens.
- **Rekonstruktion / kortlægning af noget eksisterende:** Data & evidens, Governance, Økonomi, Drift.
- **Strategi:** Strategi & marked, Økonomi, Risiko, Teknologi.

## Domænelinser
En domæne-skill (se `domaene-skill-skabelon`) kan definere egne linser i sin `references/domaenekontekst.md`. De bruges i stedet for eller sammen med standardlinserne. Kontrollér stadig MECE.

## MECE-test
Tag det fund, der er sværest at placere. Hvis det passer i to linser, så stram grænserne ("Ikke"-kolonnen) i linse-briefene. Hvis det ikke passer nogen steder, mangler der en linse.
