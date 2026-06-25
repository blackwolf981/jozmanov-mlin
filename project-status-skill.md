---
name: project-status-skill
description: Skill za pisanje in posodabljanje PROJECT_STATUS.md v projektu Jožmanov Mlin (prodaja posestva). Uporabi kadar (1) začenjaš novo sejo in bereš status, (2) ob koncu seje predlagaš posodobitev, (3) pišeš nov PROJECT_STATUS.md za projekt.
---

# project-status-skill

## Namen
`PROJECT_STATUS.md` je most med Cowork (Claude.ai desktop app) in Code (Claude Code v terminalu). Oba ga bereta, oba ga posodabljata. Je edina točka resnice o stanju projekta.

## Pravila
- **Kratko** — samo dejstva, brez razlag (razlage so v skill datotekah).
- **"Next" sekcija je obvezna** — brez nje naslednja seja nima smeri.
- **File registry je obvezen** — brez njega ne veš, katera datoteka je sveža (lokalno vs. repo vs. live).
- **Cena = NA POVPRAŠEVANJE** povsod v javnih gradivih; interni razpon ostane samo v statusu.

## Format

```markdown
# PROJECT_STATUS — Jožmanov Mlin (prodaja posestva)
_Zadnja posodobitev: YYYY-MM-DD_

## Cilj
[ena vrstica]

## Deliverabli
| Deliverable | Status | Opomba |
|-------------|--------|--------|
| Spletna stran | ✓/▶/○ | [ena vrstica] |
| Brošura (PDF) | ✓/▶/○ | |
| Maili + plan ogledov | ✓/▶/○ | |
| Prodajna strategija | ✓/▶/○ | |

## Spletna stran — podrobno stanje
- Arhitektura: single-file render iz JSON vsebine (`content_sl.json` → `build.py` → `index.html`) + `assets/` (relativne povezave).
- i18n: `lang="sl"` + JS preklop; `content_en.json` se doda kasneje (zaenkrat prazen `en`).
- Repo: [pot] · GitHub Pages: [URL ali —]
- Domene: jozmanov-mlin.com [○], jozmanovmlin.com [○], .si [○]  (○ = še ni urejeno)
- Cena: NA POVPRAŠEVANJE.

**Naslednji web korak:** [kaj je next za stran]

## File registry
| Datoteka | Lokalno | Repo | Live | Kdo ureja | Zadnji sync |
|----------|---------|------|------|-----------|-------------|
| `index.html` | ✓/— | ✓/— | ✓/— | Code | YYYY-MM-DD |
| `content_sl.json` | ✓/— | ✓/— | — | Cowork/Code | YYYY-MM-DD |
| `content_en.json` | ✓/— | — | — | (kasneje) | — |
| `build.py` | ✓/— | ✓/— | — | Code | YYYY-MM-DD |
| `PROJECT_STATUS.md` | ✓ | ✓/— | — | oba | YYYY-MM-DD |

> ⚠️ Če se datumi sync ne ujemajo — najprej uskladi (build/commit/upload) preden delaš naprej.

## Zadnja seja (YYYY-MM-DD, Cowork/Code)
- [kaj je bilo narejeno — bullet točke]

## Next
- [ ] [konkretna naloga 1]
- [ ] [konkretna naloga 2]

## Odprta vprašanja
- [vprašanje ali odločitev, ki čaka]

## Diagram
Zadnji state diagram: YYYY-MM-DD — ob branju ponudi prikaz.

## Workflow reminder
- **Cowork (app)** = strategija, vsebina, odločitve, GLEDA slike/screenshote → piše HANDOFF za Code.
- **Code (terminal)** = gradnja, build.py, popravki, git commit, deploy na GitHub.
- Ob začetku seje: preberi PROJECT_STATUS.md (+ aktualen index.html, če Code).
- Ob koncu seje: posodobi PROJECT_STATUS.md.
```

## Kdaj posodobiti

### Cowork (app) — ob koncu seje predlaga:
```
Posodobi PROJECT_STATUS.md:
- Zadnja seja: [datum, Cowork] — [kaj sva naredila / odločila]
- Next: [konkretne naloge za Code ali naslednjo sejo]
- File registry: [če se je kaj spremenilo glede vsebine/odločitev]
```

### Code (terminal) — po implementaciji:
```
Posodobi PROJECT_STATUS.md:
- Zadnja posodobitev: [današnji datum] (na vrhu)
- Zadnja seja: [datum, Code] — [kaj je bilo implementirano + deployano]
- Deliverabli: posodobi status vrstice
- File registry: posodobi "Zadnji sync" datum ZA VSAKO datoteko, ki si jo spremenil
  (vključno s PROJECT_STATUS.md samim — če pišeš vanj, posodobi tudi njegov sync)
- Next: odkljukaj opravljeno, dodaj novo
```

**Pomembno:** Datum na vrhu (`_Zadnja posodobitev:_`), datum "Zadnja seja" in vsi "Zadnji sync" datumi v File registry za spremenjene datoteke se MORAJO ujemati. Nekonzistentni datumi pomenijo, da bo naslednja seja začela z napačno predpostavko o tem, katera verzija je sveža.

## Diagram protocol
- Prvič: Claude oceni, kdaj je projekt zrel, in **predlaga** diagram (npr. flow prodajnega procesa ali arhitektura strani).
- Ob naslednjih sejah: ko prebere STATUS in vidi "Diagram:" vrstico, **vpraša** "Ali naj prikažem diagram?"
- Diagram se vsakič generira svež iz podatkov v STATUS — ne shranjujemo slike.
