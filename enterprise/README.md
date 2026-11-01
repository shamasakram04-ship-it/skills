# enterprise-prisme (v0.1.0, første udkast)

Et Claude Code-plugin til enterprise-arbejde. Det analyserer **prismatisk**: hvert problem bliver set gennem flere uafhængige linser af parallelle agenter, der alle kører på **Opus 5.5** (`claude-opus-5-5`). Derefter samler en syntese-agent fundene, og et red-team angriber resultatet, før det bliver leveret.

```
opgave → afklar → [linse 1 | linse 2 | linse 3 | …]  (parallelle Opus-agenter)
                         ↓
                      syntese  (Minto-pyramide, konflikter synlige)
                         ↓
                      red-team (hold / justér / omskriv, max én omskrivning)
                         ↓
                      levering (svaret først, F/Fo/H/V-evidens, valideringsbehov)
```

## Indhold
| Del | Type | Formål |
|---|---|---|
| `prisme-orkestrator` | auto-skill | Hovedindgang for analyser, beslutningsoplæg, strategi og rapporter |
| `skill-vurdering` | auto-skill | Vurderer skills og plugins mod en 12-punkts enterprise-rubrik |
| `auto-skill-fabrik` | auto-skill | Laver en arbejdsgang eller en claude.ai-skill om til en ny auto-skill i plugin'et |
| `domaene-skill-skabelon` | skabelon | Kopieres og udfyldes for hvert domæne (rolle, scope, linser, templates, QA) |
| `linse-analytiker`, `syntese`, `red-team` | agenter | Alle låst til `model: claude-opus-5-5` |
| `/prisme`, `/vurder-skills` | kommandoer | Eksplicit kørsel |

## Installation
```bash
# i Claude Code
/plugin marketplace add shamasakram04-ship-it/skills
/plugin install enterprise-prisme@enterprise-skills
```
Lokal test uden installation: `claude --plugin-dir ./enterprise`.

Hvis hovedsessionen også skal køre på Opus 5.5, så kopiér `settings.example.json` til projektets `.claude/settings.json`. Du kan også køre `/model claude-opus-5-5`.

## Kom i gang med dit domæne
1. Skriv: *"Lav en skill til [mit domæne] ud fra skabelonen"*. Så aktiveres `auto-skill-fabrik`.
2. Udfyld eller godkend `references/domaenekontekst.md` med aktører, begreber, systemer og domænelinser.
3. Kør `/vurder-skills enterprise/skills/<navn>`, og ret indtil scoren er mindst 10/12.
4. Prøv det af med `/prisme <et rigtigt spørgsmål fra dit domæne>`.

## Principper
- **Svaret først**, derefter en Minto-pyramide og en MECE-struktur.
- **Evidensdisciplin:** F (fakta med kilde), Fo (fortolkning), H (hypotese), V (valideringsbehov). Ingen opdigtede tal.
- **MCP'er bruges kun til at læse.** Der skrives kun til eksterne systemer, når brugeren beder om det. Se `skills/prisme-orkestrator/references/mcp-katalog.md`.
