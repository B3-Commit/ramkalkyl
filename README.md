# Ramkalkyl B3Commit 2026

Interaktiv webbapplikation för löneberäkning inom B3Commit-modellen. Konverterad från Excel till en responsiv webbapp med B3:s visuella profil.

## Vad är Ramkalkyl?

Ramkalkylen hjälper konsulter att beräkna sin nettolön, ramkostnad och överskott baserat på bruttolön och individuella val kring bil, pension, semester och andra förmåner. Alla beräkningar bygger på **skattetabell 35** för bosatta i **Örebro** med medlemskap i **Svenska Kyrkan**.

## Funktioner

- **Tre beräkningslägen** — 25, 30 eller valfritt antal semesterdagar
- **Redigerbara parametrar** — fast ramintäkt, timpris, procentsats, månadstimmar, buffert, bilförmån, pension med mera
- **250 lönenivåer** — bruttolön från 30 001 kr till 79 801 kr i steg om 200 kr
- **Automatisk beräkning** av skatt, nettolön, sociala avgifter, semester, pension (ITP1), SLP, ramkostnad och överskott
- **Skattetabell 35** med korrekt XLOOKUP-beteende (exakt eller närmast lägre)
- **Pensionsberäkning** enligt ITP1: 4,5% under brytgränsen (52 125 kr), 30% över
- **Responsiv tabell** med horisontell scroll och sticky första kolumn

## Beräkningsmodell

| Kolumn | Formel |
|---|---|
| Nettolön | Brutto − Skatt (via skattetabell) |
| Sociala avgifter | (Brutto + Förmåner) × 31,42% |
| Semester | Semestertillägg × 1,3142 |
| Pension (ITP1) | 4,5% under 52 125 kr, 30% över |
| SLP | Pension × 24,26% |
| Ramkostnad | Brutto + Soc.avg + Semester + Pension + SLP + Buffert + Bil + Övrigt |
| Överskott fast | Fast ramintäkt − Ramkostnad |
| Överskott rörlig | (Timpris × Timmar × Procent/100) − Ramkostnad |

## Teknik

Applikationen är en **enda HTML-fil** utan byggsystem. React och Babel laddas från CDN och JSX kompileras direkt i webbläsaren.

- React 18 (via CDN)
- Work Sans (Google Fonts)
- B3 brandprofil: Turquoise `#0CCCCC`, Pink `#DF668A`, rundade hörn 24px

## Deployment

Sidan publiceras automatiskt via **GitHub Pages** vid push till `main`-branchen. GitHub Actions-workflowen hanterar deploy utan manuella steg.

**Live:** [https://b3-commit.github.io/ramkalkyl/](https://b3-commit.github.io/ramkalkyl/)

## Lokal utveckling

Öppna `index.html` direkt i webbläsaren — ingen installation krävs.

```bash
# Eller använd en lokal server
npx serve .
```

## Ursprung

Konverterad från Excel-filen *Ramkalkyl B3Commit 2026 (utan semesteravsättning)* med identiska formler och skattetabelldata.
