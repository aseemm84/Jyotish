# LearnHoro — a Jyotiṣa reference built on Brihat Parashara Hora Shastra

A static, source-grounded reference site for classical Vedic astrology, plus two interactive tools:
a **kundli builder** that computes a complete chart in the browser, and a filterable table of the
**108 nakshatra padas**.

**Live site:** https://aseemm84.github.io/Jyotish/

---

## What's here

### Reference pages
Fourteen topic pages covering the framework of *Brihat Parashara Hora Shastra* (Santhanam translation):

| Page | Covers |
| --- | --- |
| Grahas | the nine planets — significations, temperament, natural benefics and malefics |
| Dignity | exaltation, debilitation, Moolatrikona, the three tiers of friendship, combustion, the nodes |
| Rashis | the twelve signs and the classifications that drive later technique |
| Bhavas | house significations, functional classes, bhava lords, how a house prospers or breaks |
| Lagna | the rising sign and the computed special ascendants |
| Vargas | all sixteen divisional charts, with the significance of each house inside each chart |
| Aspects | graha dṛṣṭi and rashi dṛṣṭi, kept distinct |
| Strength | every Shadbala component, Bhava Bala, Ishta/Kashta, Vimsopaka |
| Special Points | arudhas, argala, both karaka schemes, Karakamsa |
| Yogas | the full catalogue — Mahapurusha, Nabhasa, Raja, Dhana, Parivartana and more |
| Avasthas & Longevity | the five avastha schemes; longevity and maraka, handled academically |
| Dashas | Vimshottari with worked examples, plus the conditional and rasi dashas |
| Ashtakavarga | bindus, BAV and SAV, kakshas, the three shodhanas |

### Build a Kundli
Enter birth details and get a full technical report — **computed entirely in your browser**.
No account, no API key, no server, and it works offline.

Eighteen sections: birth particulars and pañcāṅga · rāśi chart in both North and South Indian
styles · navāṃśa · grahas with dignity and state · avasthās in four schemes · bhāvas · graha
dṛṣṭi · ashtakavarga with the three shodhanas · all sixteen vargas as charts · ṣoḍaśavarga
strength · ṣaḍbala · Sudarśana Chakra · the three friendship chakras · yogas · kārakas and
ārūḍhas · the Vimśottarī tree down to pratyantardaśā across 120 years · current transits.

Each section carries a plain-language **study note** composed from the site's own rules, with
links back to the reference page the rule came from. Print to PDF or download the raw JSON.

### 108 Nakshatra Padas
Every pada with its rāśi, navāṃśa, Vimśottarī lord, deity, symbol, gaṇa and naming syllable,
a per-graha reading grid, and a bhāva overlay. Also available in Hindi.

---

## How the chart is computed

| Layer | Source |
| --- | --- |
| Planetary positions | [astronomy-engine](https://github.com/cosinekitty/astronomy) (MIT), inlined |
| Ayanāṃśa | Lahiri, as a quadratic fitted to Swiss Ephemeris (agrees to ~0.01″) |
| Lagna | sidereal time and obliquity; within ~0.3′ of Swiss Ephemeris |
| Everything else | derived here from those positions using the classical rules |

Accuracy was validated against Swiss Ephemeris and against printed charts from
Parashara's Light. Tithi, yoga, karaṇa, the time reductions, the Avakhaḍa chakra and Bhabhoga
match that software exactly; planetary longitudes agree with Swiss Ephemeris to well under an
arcminute — finer than a nakshatra pāda (3°20′) or a D60 amsa (30′).

**Stated simplifications**, also flagged in the page itself:

- Dṛk Bala uses the graded whole-sign glance, not the exact Virupa-by-angle formula.
- Nathonnatha is measured from clock noon rather than local apparent noon.
- Sunrise/sunset is accurate to a few minutes; Iṣṭakāla inherits that tolerance.
- Vimśopaka is a transparent index in the spirit of the classical one, not the canonical weighting.
- Ārūḍha exception cases follow the rule given on the Special Points page.
- The twelve Śayanādi avasthās are omitted — they need the person's name-syllable.

An optional **cross-check** can fetch the same chart from an external ephemeris service and
report how far the two sources disagree.

---

## Source discipline

Three layers are kept distinct throughout, and labelled wherever they appear:

1. **BPHS text** — what the translated verses state, cited by chapter.
2. **Translator/commentary** — notes in the Santhanam edition.
3. **Study notes** — plain-language synthesis, or later analytical practice, added here.

Where editions or lineages disagree, the site says so rather than picking a side silently.
Verse numbers are OCR-affected in the source PDFs, so chapters are cited and verse numbers
should be confirmed against the text.

---

## Running it

It is a plain static site — no build step, no dependencies, no server.

```bash
git clone https://github.com/aseemm84/Jyotish.git
cd Jyotish
python3 -m http.server 8000     # then open http://localhost:8000
```

Every page is a single self-contained HTML file with its CSS and JavaScript inlined, so you can
also just open a file directly in a browser. Deployment is GitHub Pages from the repository root.

---

## Scope and limits

This is an **educational reference on traditional doctrine**. It is not a scientific claim, and
not a prediction about any person. Nothing here forecasts health, illness, lifespan, wealth,
marriage, children or misfortune; classical indications are conditional by nature and are
presented as material for study.

For medical, legal, financial, relationship or safety matters, consult a qualified professional.

---

## Credits

- Primary source: *Brihat Parashara Hora Shastra*, R. Santhanam translation.
- Positions: [astronomy-engine](https://github.com/cosinekitty/astronomy) by Don Cross (MIT).
- City lookup: [Open-Meteo](https://open-meteo.com/) geocoding API.
- Optional cross-check: [bharatephemeris.com](https://bharatephemeris.com).
