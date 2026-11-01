# Rubrik: enterprise-skill (0–2 pr. kriterium, max 12)

**0** = mangler eller er forkert · **1** = delvist på plads · **2** = solidt

## 1. Trigger (description)
- 2: Siger både *hvad* skillen gør og *hvornår* den skal bruges. Har konkrete triggerord og -situationer (også indirekte formuleringer) og siger hvornår den *ikke* skal bruges. Højst ca. 1024 tegn.
- 1: Siger hvad den gør, men har svage eller få triggere.
- 0: Er vag eller generisk eller bare en liste af emner. Ingen "brug når".

## 2. Scope
- 2: Brødteksten har eksplicit *scope* og *ikke-scope*, og en klar rolle eller identitet.
- 1: Scope kan udledes, men står ingen steder.
- 0: Uafgrænset, så den kan trække alt ind.

## 3. Progressive disclosure
- 2: SKILL.md er under ca. 500 linjer, detaljer ligger i `references/`/`templates/`, og brødteksten siger hvornår hver fil skal læses. Ingen dubletter.
- 1: Er lidt for lang, eller referencerne er ikke forklaret.
- 0: Alt ligger i én stor fil, eller den henviser til filer der ikke findes.

## 4. Metode og output
- 2: Har en fast arbejdsgang i trin, et defineret outputformat og kvalitetskriterier (fx answer-first, MECE, QA-tjekliste).
- 1: Har en arbejdsgang, men intet outputformat, eller omvendt.
- 0: Kun en stilbeskrivelse.

## 5. Sikkerhed og evidens
- 2: Har evidensregler (F/Fo/H/V eller tilsvarende), forbud mod at opdigte, og regler for eksterne skrivehandlinger (kun når brugeren beder om det). Ingen hemmeligheder eller persondata i filerne.
- 1: Har dele af det.
- 0: Har ingen af delene, eller indeholder følsomme data.

## 6. Drift (agenter, model, vedligehold)
- 2: Agenter har fast `model` (enterprise-standard: `claude-opus-5-5`) og et snævert ansvar. Plugin har version. Skillen kan testes med en eksempel-prompt.
- 1: Delvist.
- 0: Uklart hvilken model eller agent der bruges, og intet versionsnummer.
- *Gælder ikke rene SKILL.md-skills uden agenter. Scor dem på versionering og testbarhed alene.*
