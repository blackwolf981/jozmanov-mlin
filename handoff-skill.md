---
name: handoff-skill
description: Skill za pisanje handoff dokumentov v projektu Jožmanov Mlin — strukturiranih MD datotek, ki Code (Claude Code) jasno razložijo nalogo na spletni strani ali drugem deliverablu. Uporabi kadar (1) Cowork in Code morata komunicirati o kompleksni nalogi, (2) Code rabi kontekst, ki ga ni mogoče opisati v kratkem promptu, (3) Cowork delegira gradnjo/popravek strani, ki vključuje vizualni namen (slike, postavitev), ki ga Code ne vidi.
---

# handoff-skill

## Namen
Handoff dokument je datoteka v repo, ki jo Code prebere in takoj razume — brez dolgega tekstovnega prompta. Cowork ga pripravi, Code ga izvede. Most teče v eno smer: **Cowork → handoff → Code**.

## Zakaj je handoff potreben (Cowork vidi, Code ne)
Cowork (desktop app) **vidi slike in screenshote** — zato presoja postavitev, izbor fotk, vizualni vtis. Code **NE vidi vizualnega rezultata**. Zato Cowork v handoffu vizualni namen **opiše z besedami**: katera slika, kam, kako velika, kakšen občutek.

## Kaj Code razume
- ✓ Markdown (.md) — struktura, tabele, koda, seznami
- ✓ JSON — sheme, vsebina (`content_sl.json`), podatkovne strukture
- ✓ HTML/CSS/JS koda — bere in piše
- ✓ HTML komentarji — tehnične opombe v kodi
- ✗ Rendered HTML — vidi kodo, ne vizualnega rezultata
- ✗ Slike — ne vidi vsebine fotografij (le imena datotek/poti)
- ✗ Vizualni vtis — razume logiko in strukturo, ne izkušnje

## Format handoff dokumenta

```markdown
# HANDOFF: [naziv naloge]
_Datum: YYYY-MM-DD | Pripravil: Cowork | Za: Code_

## Cilj
[En stavek: kaj mora Code narediti]

## Kontekst
[Zakaj to delamo — max 3 bullet točke]

## Stanje pred implementacijo
- Aktivni file(i): `index.html`, `content_sl.json`, `build.py`
- Sekcija strani: [hero / o posestvu / galerija / kontakt / ...]
- Razpoložljivi assets: `assets/img/[imena]`, `assets/video/[imena]`
- i18n ključi, ki jih naloga doda: [`hero.title`, ...]

## Kar je treba narediti
### [Korak 1]
[Opis koraka]

### [Korak 2]
[Opis koraka]

## Vsebina za implementacijo
[JSON izsek za content_sl.json ALI tabela: ključ → slovensko besedilo]
[Vsi novi vidni teksti dobijo i18n ključ; en-vrednost pusti prazno ("").]

## Vizualni namen (ker Code ne vidi slik)
- Slika `assets/img/Mlin_01.jpg` → hero ozadje, polna širina, temni overlay za berljiv naslov.
- [opiši vsako pomembno sliko/postavitev z besedami]

## Preverjanje po implementaciji
- [ ] `build.py` zgenerira `index.html` brez napak
- [ ] Vsi novi teksti imajo `data-i18n` ključ (EN lahko prazen)
- [ ] Render OK na 380px (mobilno) in desktop
- [ ] Vse slike/povezave delujejo (relativne poti)
- [ ] Cena ni nikjer izpisana — samo "na povpraševanje"
- [ ] git commit + push (+ deploy, če je GitHub Pages aktiven)

## Opombe
[Kar ne sme iti narobe / znane pasti]
```

## Kdaj napisati handoff

Napiši handoff ko:
- Cowork delegira gradnjo/večjo spremembo sekcije strani (vsebina + postavitev sta kompleksni).
- Naloga vključuje izbor in razporeditev slik (Code potrebuje besedni opis vizualnega namena).
- Je naloga večkoračna in zahteva natančen vrstni red.
- Razlagaš arhitekturno odločitev (npr. struktura `content_*.json`, build flow).

Ne piši handoff ko:
- Je naloga enostavna (Code jo razume iz kratkega prompta).
- Gre za popravek manjše napake (direkten prompt je hitrejši).

## Lokacija v repo
```
jozmanov-mlin/
└── handoffs/
    └── HANDOFF_[datum]_[naziv].md
```

Code prebere: `"Preberi handoffs/HANDOFF_2026-06-25_galerija.md in implementiraj"`

## Primer — nova sekcija strani

```markdown
# HANDOFF: Galerija posestva
_Datum: 2026-06-25 | Pripravil: Cowork | Za: Code_

## Cilj
Dodaj galerijo fotografij posestva v index.html (sekcija pod "O posestvu").

## Stanje pred implementacijo
- Aktivni file: index.html + content_sl.json + build.py
- Razpoložljivi assets: assets/img/ (Mlin_*, Kasca_*, Kopalisce_*, Loka_*, Jez_*)
- Novi i18n ključi: galerija.naslov, galerija.podnaslov

## Vsebina
| Ključ | SL besedilo |
|-------|-------------|
| galerija.naslov | Posestvo v sliki |
| galerija.podnaslov | Mlin, kašča, kopališče na Krki |

## Vizualni namen (ker Code ne vidi slik)
- Grid 3 stolpci (desktop), 1 stolpec (mobilno).
- Vrstni red poudarka: Mlin_01 (glavna), Kopalisce_pod_slapom_01, Kasca_01, Jez_ob_mlinu_01.
- Lightbox ob kliku; lazy-load.

## Preverjanje
- [ ] build.py OK
- [ ] data-i18n na naslovih (en prazen)
- [ ] Render na 380px
- [ ] Vse slike naložene (relativne poti)
- [ ] git push
```
