---
name: auto-skill-fabrik
description: Laver en beskrevet arbejdsgang, et fagområde eller en eksisterende prompt om til en ny auto-aktiverende skill i enterprise-prisme-plugin'et, ud fra domæne-skabelonen, og kvalitetssikrer den med skill-vurdering. Brug når brugeren vil "lave en skill", "gøre det her til en skill", "automatisere denne arbejdsgang", "lave en custom/auto skill", konvertere en claude.ai-skill eller prompt til plugin-format, eller tilføje et nyt domæne til enterprise-setup'et.
---

# Auto-skill-fabrik

## Arbejdsgang
1. **Indsaml.** Find ud af følgende. Hvis brugeren allerede har givet materiale (en prompt, en eksisterende SKILL.md, dokumenter, en samtale), så udled svarene derfra, før du spørger:
   - Hvilke opgaver skal skillen løse? Giv 3 eksempler på rigtige forespørgsler.
   - Hvad skal den ikke bruges til?
   - Hvilken rolle har den, hvilke begreber bruger den, hvilke kilder og systemer (MCP'er)?
   - Hvad er outputformatet, og hvem læser det?
   Spørg kun om det, du ikke kan udlede. Stil højst 4 spørgsmål på én gang.
2. **Navngiv.** Navnet skal være kebab-case (a-z, 0-9, bindestreg), højst 64 tegn og beskrive hvad skillen gør. Tjek at navnet ikke allerede findes i `enterprise/skills/`.
3. **Byg.** Kopiér `enterprise/skills/domaene-skill-skabelon/` til `enterprise/skills/<navn>/`. Udfyld alle `[FELTER]`, og fjern vejledningskommentaren og de kursive hjælpelinjer.
   - **Description:** hvad + hvornår (konkrete triggerord, også indirekte formuleringer) + hvornår ikke. Højst ca. 1024 tegn.
   - Lang viden lægges i `references/`. Selve SKILL.md skal holdes under ca. 200 linjer.
   - Har skillen brug for en specialiseret agent, så tilføj `enterprise/agents/<navn>.md` med `model: claude-opus-5-5` og et snævert ansvar.
4. **Validér.**
   - Kør `python3 skills/.system/skill-creator/scripts/quick_validate.py enterprise/skills/<navn>`.
   - Kør `skill-vurdering` på den nye skill. Målet er mindst 10/12. Ret og vurdér igen højst to gange.
   - Lav en triggertest: skriv 3 forespørgsler, der skal aktivere skillen, og 2, der ligner, men ikke skal. Sammenlign med de andre skills' descriptions, og skriv det ned, hvis de overlapper.
5. **Versionér.** Hæv `version` i `enterprise/.claude-plugin/plugin.json` (minor for en ny skill). Commit kun, hvis brugeren har bedt om det.

## Konvertering fra claude.ai-skill
En claude.ai-skill (en mappe med `SKILL.md`) kan bruges direkte. Kopiér den til `enterprise/skills/`, tjek at frontmatter-navnet er det samme som mappenavnet, og kør derefter trin 4. Behold referencefilerne. Fjern persondata og projektfortrolige oplysninger, før den committes til et delt repo.
