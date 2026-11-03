<!-- agentic-starter-kit -->
# Agentic Starter Kit

Technologicky neutrální sada šablon a promptů pro vývoj aplikace agenty ve
spolupráci s člověkem. Obsahuje **systém práce** (pravidla, evidence, životní
cyklus, vstupní prompty) – neobsahuje specifikaci ani implementaci žádné
aplikace.

## Obsah

```
.github/
  prompts/
    bootstrap-agentic-environment.prompt.md   # jednorázové založení prostředí
    discover-project.prompt.md                # discovery → SPEC.md
    plan-increment.prompt.md                  # návrh řešení + úkoly
    work-task.prompt.md                       # realizace jednoho úkolu
  templates/agentic/
    AGENTS.md        # provozní řád (jediný zdroj pravidel)
    README.md        # README cílového projektu
    PROJECT.md       # fáze, bod pokračování, otázky
    SPEC.md          # požadavky, omezení, AC
    TASKS.md         # úkoly a důkazy
    DECISIONS.md     # rozhodnutí a schválení
```

Prompty jsou anglicky (přesnější instrukce pro model), generované dokumenty
a komunikace s člověkem jsou česky. Identifikátory a stavy jsou ASCII slugy.

## Použití

### A. Nový projekt v tomto repozitáři

1. Zkopíruj nebo naklonuj kit jako základ projektu.
2. Ve VS Code (GitHub Copilot, agentní režim) spusť
   `/bootstrap-agentic-environment` s argumentem např. `write`.
3. Agent zkopíruje šablony do kořene, doplní placeholdery, přepíše tento
   README šablonou a nastaví fázi `pripraveno-ke-specifikaci`.
4. Pokračuj příkazem `/discover-project`.

### B. Existující repozitář

1. Zkopíruj celý adresář `.github/` do cílového repozitáře.
2. Spusť `/bootstrap-agentic-environment` (výchozí režim `propose` ukáže,
   co by vzniklo; `write` zapíše).
3. Existující dokumenty bootstrap nepřepisuje – navrhne jen chybějící části.

### C. Jiný nástroj než VS Code

Předej agentovi tělo `bootstrap-agentic-environment.prompt.md` jako zadání.
Prompt podle nástroje umístí vstupní postupy do `docs/workflows/` místo
`.github/prompts/`.

## Placeholdery v šablonách

| Token | Nahrazuje se |
| --- | --- |
| `{{PROJECT_NAME}}` | název projektu |
| `{{LANGUAGE}}` | jazyk dokumentace (česky, např. `čeština`) |
| `{{APPROVER}}` | osoba/role, která schvaluje |
| `{{DATE}}` | datum bootstrapu `RRRR-MM-DD` |

## Údržba

- Pravidlo procesu měň v `templates/agentic/AGENTS.md`, ne v promptech.
- Formát záznamu měň v příslušné šabloně (`TASKS.md`, `DECISIONS.md`…).
- Prompty drž krátké; odkazují na sekce `AGENTS.md` a neopisují je.
- Frontmatter `agent: agent` vyžaduje VS Code ≥ 1.105; pro starší verze
  použij `mode: agent`.
