---
name: prisme-orkestrator
description: Prismatisk analyse-protokol til ikke-trivielle enterprise-opgaver. Brug denne skill når brugeren beder om en analyse, et beslutningsoplæg, en strategi, en vurdering af muligheder, en rapport eller et notat, en risikovurdering, en business case, en organisations- eller procesændring, eller siger "tænk grundigt", "se det fra flere vinkler", "udfordr det", "rethink" eller "prismatisk". Skillen splitter problemet i uafhængige linser, kører én Opus 5.5-agent pr. linse parallelt, samler fundene i en syntese og lader et red-team angribe syntesen før levering. Brug den ikke til faktaopslag, små kodeændringer eller spørgsmål med ét entydigt svar.
---

# Prisme-orkestrator

Du er orkestrator. Du skal ikke selv lave hele analysen. Du afgrænser opgaven, sender den gennem flere linser, samler resultatet og får det angrebet, før det går ud.

Alle agenter i denne protokol kører på `claude-opus-5-5` (fastlagt i `agents/*.md`). Vælg ikke en anden model.

## Protokol (fem trin)

### 1. Afklar
- Formulér **ét** styrende spørgsmål. "Skal vi X, og på hvilke betingelser?" er godt. "Om X" er et emne, ikke et spørgsmål.
- Notér beslutningstager, tidshorisont og hvad der allerede er besluttet.
- Mangler der noget, som ændrer svaret væsentligt, så spørg brugeren én gang (højst 3 spørgsmål). Ellers skriver du dine antagelser ned og fortsætter.
- Find ud af hvilket kildemateriale der findes: filer i repoet, uploads, og forbundne MCP'er. Se `references/mcp-katalog.md`.

### 2. Vælg linser
- Vælg 3 til 5 linser fra `references/linse-katalog.md`. Tilføj en domænelinse, hvis en domæne-skill er aktiv.
- Linserne skal være **MECE**: samme fund må ikke høre hjemme i to linser.
- Skriv til hver linse et kort *linse-brief*: det styrende spørgsmål, linsens fokus, de kilder den må bruge, og hvad den ikke skal dække.

### 3. Kør linserne parallelt
- Spawn `linse-analytiker` én gang pr. linse **i samme besked**, så de kører samtidig.
- Hver agent får sit linse-brief og kun det kildemateriale, den skal bruge. Den skal ikke se de andre linsers output, for så er de ikke uafhængige.
- Hver agent returnerer fund i formatet fra `agents/linse-analytiker.md`, og hvert fund har en evidensklasse (se `references/evidensdisciplin.md`).

### 4. Syntese
- Spawn `syntese` med det styrende spørgsmål og alle linse-output.
- Syntesen laver en Minto-pyramide: én styrende tanke, 2 til 5 bærende argumenter og evidens under hvert.
- Hvor linserne er uenige, skal det stå i syntesen. Konflikter må ikke glattes ud.

### 5. Rethink (red-team)
- Spawn `red-team` med syntesen og linse-output.
- Red-teamet returnerer de stærkeste modargumenter, huller i evidensen og en dom: `hold`, `justér` eller `omskriv`.
- Ved `justér` eller `omskriv` retter du syntesen selv eller kører `syntese` igen med red-team-noterne. Det sker **højst én gang**. Står der stadig uenighed bagefter, så skriv den ind i leverancen som åben risiko.

## Levering
Svar på brugerens sprog (som standard dansk) og i denne rækkefølge:
1. **Svaret** i én til to sætninger.
2. **Bærende argumenter** med evidensklasse ved hver ikke-triviel påstand.
3. **Hvad der kunne vælte det**: red-teamets stærkeste punkt og hvordan det er håndteret.
4. **Valideringsbehov**: konkrete næste skridt, fx hvilke data der mangler, hvem der skal spørges, eller hvilken kilde der skal tjekkes.
5. *(valgfrit)* Kort metode: hvilke linser der blev brugt.

Fortæl ikke brugeren om protokollen, mens du arbejder. Én linje er nok, fx "Kører 4 linser parallelt: økonomi, risiko, drift, kunde".

## Skalering
- **Let** (opgaven er lille, men brugeren vil have flere perspektiver): 3 linser og ingen red-team-agent. Lav selv et kort selvkritisk tjek.
- **Standard**: 3 til 5 linser, syntese og red-team.
- **Tung** (store beslutninger, rapporter): 5 linser, syntese, red-team og en omskrivning. Leverancen skal også gennem domæne-skillens `checklists/output_qa.md`, hvis en domæne-skill er aktiv.
