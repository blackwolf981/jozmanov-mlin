# PROJECT_STATUS — Jožmanov Mlin (prodaja posestva)
_Zadnja posodobitev: 2026-06-25_

## Cilj
Prodaja celotnega posestva Jožmanov mlin **v kosu** enemu investitorju, ki bo mlin obnovil (smer turizem).

## Deliverabli
| Deliverable | Status | Opomba |
|-------------|--------|--------|
| Spletna stran | ▶ | v1 stoji (`index.html` + `assets/`), čaka pregled + prehod na build/JSON arhitekturo |
| Brošura (PDF) | ○ | nova draft `.docx` prebrana = smer "investicijska priložnost", krajše |
| Maili + plan ogledov | ○ | za poletne oglede jul–sep 2026 |
| Prodajna strategija | ○ | vključ. argumentacija cene (ni uradne cenitve) |

(✓ končano · ▶ v teku · ○ ni začeto)

## Spletna stran — podrobno stanje
- Arhitektura (dogovor 2026-06-25): vsebina ločena v `content_sl.json` → `build.py` zgenerira `index.html` + `assets/` (relativne povezave, ne base64).
- i18n: `lang="sl"` + JS preklop SL/EN. `content_en.json` se doda kasneje (zaenkrat prazen `en`, brez prevoda vsebine). SEO `hreflang` pripravljen/zakomentiran.
- Hosting: start na **GitHub (Pages)**; kasneje pravo gostovanje + domene.
- Domene (želene): jozmanov-mlin.com [○], jozmanovmlin.com [○], .si [○].
- Cena: **NA POVPRAŠEVANJE** (nikjer izpisana).
- Vizualije: zaenkrat telefonske fotke za demo; profi foto/video kasneje. Gradi modularno za menjavo slik.

**Naslednji web korak:** Andrej pregleda v1 → zbere popravke; nato prehod na `content_sl.json` + `build.py` in init GitHub repo.

## File registry
| Datoteka | Lokalno | Repo | Live | Kdo ureja | Zadnji sync |
|----------|---------|------|------|-----------|-------------|
| `index.html` | ✓ | — | — | Code | 2026-06-24 |
| `content_sl.json` | — | — | — | Cowork/Code | — (še ni) |
| `content_en.json` | — | — | — | (kasneje) | — |
| `build.py` | — | — | — | Code | — (še ni) |
| `assets/img,video` | ✓ | — | — | Code | 2026-06-24 |
| `PROJECT_STATUS.md` | ✓ | — | — | oba | 2026-06-25 |

> ⚠️ Repo še ni inicializiran. Build/JSON arhitektura je dogovorjena, a še ne implementirana.

## Dejstva o posestvu (reference)
- Lokacija: Drašča vas 26, 1303 Zagradec; k.o. 1437 Šmihel pri Žužemberku; dolina Krke, Dolenjska (~36 km / 30 min od lj. obvoznice). ~15.000 m².
- Parcele (v kosu): 2661/1 (del), 2662 (del), 2663, 3441, 3442, 2639, 2640/5, 2640/6.
- Objekti: mlin (stavba 455, parc. 3442, kult. spomenik EŠD 16225), kašča (458, parc. 3441), nekdanji hlev (888, parc. 2663 — ZVKDS dovoli rušitev + novogradnjo v istih gabaritih), zgodovinski objekt ob Krki (parc. 2662 — možna rekonstrukcija).
- Status: del zazidljiv (CD centralne dejavnosti, OPN DR08.ml); dovoljen turizem/gostinstvo/kultura. ZVKDS (mag. Štepec, NM) 20. 5. 2025 potrdil vizijo: butični hotel / interpretacijski center, vinska klet v kašči, glamping.
- Aduti: naravno kopališče na Krki, Rivčja jama (Natura 2000), supi/kajaki, krožne poti, 7 vodnih koles (redkost).
- Prodajalci: 5 solastnikov (Andrej = največji delež + vodja; dve teti, mama, brat). Vsi soglašajo; Andrej organizira.
- Interni cenovni razpon: **500.000–900.000 €** (NE javno; brez uradne cenitve → potrebna obranljiva argumentacija).
- Ciljni kupec: kapitalsko močan turistični investitor / HNWI / tujec. Andrejev sekundarni interes = lokalni partner/operativec po prodaji (prodajni adut za oddaljenega kupca).
- Časovnica: material TAKOJ za poletne oglede (jul–sep 2026, kopališče v polnem soju). Outreach ima Andrej; najina skrb = VSEBINA.

## Zadnja seja (2026-06-25, Cowork)
- Prilagodila skilla iz projekta anthropic-courses na Jožmanov Mlin: `project-status-skill.md`, `handoff-skill.md`.
- Dogovor o arhitekturi: vsebina v JSON → `build.py` → statičen `index.html`; i18n pripravljen za EN brez prevoda zdaj; GitHub od začetka.
- Preoblikovan ta PROJECT_STATUS v nov format (dodan File registry).

## Next
- [ ] Andrej pregleda spletno stran v1 → zbere popravke.
- [ ] Code: init git repo + GitHub, prehod na `content_sl.json` + `build.py`, vgradi i18n nastavke (prazen `en`).
- [ ] Izdelati prodajno brošuro (PDF, SL; EN kasneje).
- [ ] Maili + plan poletnih ogledov + prodajna strategija + argumentacija cene.
- [ ] (Kasneje) domene jozmanov-mlin.com / jozmanovmlin.com / .si + pravo gostovanje + prevod EN.

## Odprta vprašanja
- Jezikovni preklop: `?lang=en` vs. `/en/` poti — odločiva ob hostingu.
- Ali brošura nastane iz iste `content_sl.json` vsebine (en vir resnice) ali ločeno?

## Diagram
Zadnji state diagram: — (še ni). Ob zrelosti projekta Cowork predlaga flow prodajnega procesa ali arhitekturo strani.

## Workflow reminder
- **Cowork (app)** = strategija, vsebina, odločitve, GLEDA slike/screenshote → piše HANDOFF za Code.
- **Code (terminal)** = gradnja, `build.py`, popravki, git commit, deploy na GitHub.
- Ob začetku seje: preberi PROJECT_STATUS.md (Code tudi aktualen `index.html`).
- Ob koncu seje: posodobi PROJECT_STATUS.md (datum na vrhu + Zadnja seja + File registry sync).
