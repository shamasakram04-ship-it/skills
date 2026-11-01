---
name: skill-vurdering
description: Vurderer (assesser) eksisterende Agent Skills og Claude Code-plugins mod en enterprise-rubrik – trigger-kvalitet i description, scope og afgrænsning, overlap med andre skills, progressive disclosure, evidens- og sikkerhedsregler, model- og agentopsætning – og leverer en scorecard med prioriterede rettelser. Brug når brugeren beder om at vurdere, auditere, reviewe, sammenligne eller forbedre skills, SKILL.md-filer, agenter eller plugins, eller skriver "asses skills"/"assess skills".
---

# Skill-vurdering

## Arbejdsgang
1. **Find skills.** Kig i den sti brugeren angiver. Er der ingen sti, så brug `enterprise/skills/`, `.claude/skills/` og `skills/` i repoet. En skill er en mappe med en `SKILL.md`. Læs også `agents/*.md` og `.claude-plugin/plugin.json`, hvis de findes.
2. **Læs hver skill helt.** Det gælder frontmatter, brødtekst og referencer, som brødteksten henviser til.
3. **Scor** hver skill efter `checklists/rubrik.md` med 0–2 point pr. kriterium. Hver score skal have en begrundelse med citat eller linjehenvisning.
4. **Tjek overlap på tværs af skills.** Hvis to descriptions vil trigge på den samme forespørgsel, så skriv det med et konkret eksempel.
5. **Er der mange skills, eller skal det være grundigt,** så kør vurderingen prismatisk via `prisme-orkestrator` med linserne *trigger og scope*, *indhold og metode* og *sikkerhed og drift*.

## Output
```
# Skill-vurdering – <dato>

| Skill | Trigger | Scope | Disclosure | Metode | Sikkerhed | Drift | Total /12 |
|---|---|---|---|---|---|---|---|

## Top-3 rettelser (på tværs)
1. <rettelse> – påvirker <skills> – forventet effekt

## Pr. skill
### <navn> – <total>/12
- **Styrker:** …
- **Rettelser (prioriteret):** 1. … (konkret omskrivning af description, hvis relevant)

## Overlap
- <skill A> ↔ <skill B>: eksempel-prompt "<…>" trigger begge → forslag
```
Ret ikke i filerne, medmindre brugeren beder om det. Når du foreslår en ny description, så skriv hele teksten, så den kan kopieres direkte.
