# MCP-katalog: kapabilitet → værktøj

Find kildemateriale gennem forbundne MCP-servere, før du antager at noget mangler. Værktøjer kan være *deferred*, så søg dem frem med `ToolSearch` (fx `"notion search"`, `"drive read"`), før du konkluderer at de ikke findes. Er en server ikke forbundet, så skriv det i leverancen som et valideringsbehov. Find ikke på indhold i stedet.

**Regel:** Læs gerne. Skriv, del, slet og send kun når brugeren udtrykkeligt har bedt om det i den aktuelle opgave.

| Kapabilitet | Typiske MCP-familier | Brug til |
|---|---|---|
| Interne dokumenter og wiki | `Notion`, `Atlassian_Rovo` (Confluence), `Google_Drive`, Box/Dropbox, Microsoft 365 | Kildemateriale, politikker, tidligere leverancer |
| Opgaver og projekter | `Atlassian_Rovo` (Jira), `monday_com`, `github` | Status, beslutningslog, leverancer |
| Møder og samtaler | `Fireflies`, `Zoom_for_Claude`, Gmail/Calendar | Beslutninger, citater, aktører |
| Web-research | `Firecrawl`, `Exa`, `WebSearch`/`WebFetch` | Marked, benchmarks, regulering (tjek dato og kilde) |
| Akademisk evidens | `Elicit`, `Firecrawl` research | Litteratur og studier |
| Officiel teknisk dokumentation | `Microsoft_Learn`, `Supabase`/`Neon` docs | Tekniske påstande |
| Data og analyse | `Google_Cloud_BigQuery`, `Neon`, `Supabase` (read-only SQL) | Tal, der skal være F |
| Økonomi og regnskab | `Xero`, `Financial_Datasets` | Regnskabstal, nøgletal |
| Visualisering og leverance | `Miro`, `Figma`, `Canva`, `Claude_Docs`, Artifacts | Diagrammer, slides, dokumenter |

## Afprøvet i opsætningen (første udkast, 2026-11)
Read-only identitets- og listekald blev testet ved opsætning:

| Server | Resultat |
|---|---|
| `Notion` (`notion-get-self`) | Forbundet |
| `Atlassian_Rovo` (`atlassianUserInfo`) | Forbundet |
| `Google_Drive` (`list_recent_files`) | Forbundet |
| Plugin-MCP'er bag proxy (fx brand-voice, canva-plugin, flere finans-plugins) | Fejlede med proxy 403 i cloud-sessionen. Kør dem lokalt, eller tillad dem i miljøets netværkspolitik |

Opdatér tabellen, når opsætningen ændrer sig. Den beskriver ét miljø og gælder ikke alle.
