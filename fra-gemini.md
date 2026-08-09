> From: https://gemini.google.com/app/095a4c8f6b4401f5

# you asked

message time: 2026-08-09 18:02:49

Lige et Github spørgsmål mere. Jeg laver hjemmeside for Røde Kors Roskilde. Det gør jeg i Wordpress med et par tools jeg selv har udviklet. Dog mest Wordpress. Det bliver efterhånden temmelig omfattende og jeg skal have flere med på holdet. Det betyder dokumentation både af processer layout aftaler og så nogle særlige adresser og eventuelt koder. Det vil jeg gerne dele med 3 - 4 andre rødekors folk. Kan jeg det i Github? En wiki til dokumentation og en del readme filer og et par html kodestumper. Altså ikke public men åben for de rette personer.

---

# gemini response

Ja, det kan du sagtens, og GitHub er oplagt til netop det formål.

Du kan oprette et **privat repository** (repository = projektmappe), som kun du og de 3–4 udvalgte personer har adgang til. I et gratis GitHub-fællesskab/konto kan du invitere op til flere medarbejdere (collaborators) på et privat repository uden at betale noget.

---

### Hvad du kan samle i det private repository

1. **GitHub Wiki**
   * Hvert repository har sin egen indbyggede **Wiki**, som kan slås til.
   * Her kan du oprette sider for **procesbeskrivelser**, layoutaftaler, retningslinjer for indhold, tjeklister til nye skribenter osv.
   * Wiki-siderne skrives i Markdown, hvilket gør det nemt at overskue og redigere.

2. **README-filer og Mappestruktur**
   * I selve repositoriet kan du organisere mapper til dokumentation (f.eks. `/docs/layout-aftaler.md` eller `/docs/guider/`).
   * Hoved-`README.md`-filen kan fungere som en velkomst- og startside med links til resten af dokumentationen og wikien.

3. **HTML- og PHP-kodestumper (Code Snippets)**
   * Du kan gemme dine egne custom skabeloner, HTML/CSS-kodestumper eller WordPress-functions direkte som filer i repositoriet.
   * Det gør det nemt for andre på holdet enten at hente koden eller se historikken over ændringer (versionering).

4. **Koder, adresser og følsomme oplysninger (VIGTIGT)**
   * Selv om repositoriet er privat, bør du **undgå at gemme passwords, API-nøgler eller databasekoder direkte i fritekst** i Git-filer. Hvis I ved et uheld kommer til at lave repositoriet offentligt en dag, ligger koderne i versionhistorikken.
   * **Bedste praksis:** 
     * Brug repositoriet til *adresser* (f.eks. staging-URL, login-URL til WordPress, server-navne).
     * Gem reelle passwords/adgangskoder i en dedikeret, krypteret password-manager (f.eks. Bitwarden, 1Password eller NordPass), som I deler i teamet.
     * Alternativt kan du benytte **GitHub Secrets** (under settings) eller en krypteret fil, hvis det er nødvendigt i selve koden.

---

### Sådan kommer du i gang

1. **Opret et nyt repository:**
   * Gå til GitHub og vælg **New Repository**.
   * Giv det et navn (f.eks. `rodekors-roskilde-web-docs`).
   * Sæt markeringen til **Private**.

2. **Invitér dine kollaboratører:**
   * Gå ind under **Settings** $\rightarrow$ **Collaborators** i repositoriet.
   * Klik på **Add people** og indtast deres GitHub-brugernavne eller e-mailadresser. De modtager derefter en invitation via e-mail.

3. **Slå Wiki til:**
   * Under **Settings** $\rightarrow$ **General** ruller du ned til afsnittet *Features* og sætter flueben i **Wikis**.
   * Klik på fanebladet **Wiki** i toppen af repositoriet for at oprette den første side.

<FollowUp label="Vil du have en skabelon til, hvordan I kan strukturere wikien og README-filen?" query="Vis mig et forslag til en god mappestruktur og Wiki-opbygning til dokumentation af et WordPress-projekt på GitHub."/>

---

# you asked

message time: 2026-08-09 18:04:46

Vis mig et forslag til en god mappestruktur og Wiki-opbygning til dokumentation af et WordPress-projekt på GitHub.

---

# gemini response

Et velstruktureret setup på GitHub gør det let for nye medarbejdere at komme i gang og holde styr på både drift, aftaler og kode.

Her er et konkret forslag til, hvordan du kan opbygge henholdsvis **mappestrukturen (Git-repositoriet)** og **Wiki-strukturen**.

---

## 1. Mappestruktur i repositoriet

Repositoriet bør rumme selve koden (dine custom tools/plugins) samt overordnede guider i Markdown-format.

```text
rodekors-roskilde-web/
├── .github/
│   └── CODEOWNERS              # Angiver hvem der har ansvaret for hvad
├── custom-tools/               # Dine egne udviklede værktøjer/plugins
│   ├── min-custom-plugin/
│   │   ├── min-custom-plugin.php
│   │   └── README.md           # Teknisk intro til det specifikke plugin
│   └── child-theme/            # Eventuelle custom CSS/functions.php
├── docs/                       # Guider og manualer i Markdown
│   ├── layout-og-design.md     # Farver, skrifttyper, billedstørrelser
│   ├── redaktoer-guide.md      # Hvordan man opretter indhold i WP
│   └── server-og-adresser.md   # Overblik over servere, URL'er og logins
├── snippets/                   # HTML/CSS/PHP-kodestumper til genbrug
│   ├── header-banner.html
│   └── custom-functions.php
├── .gitignore                  # Filer Git skal ignorere (f.eks. wp-config.php)
└── README.md                   # Repositoriets forside og startpunkt
```

### Indhold i hoved-`README.md`
Forsiden af repositoriet bør fungere som en "Velkommen til"-side med hurtige genveje:

```markdown
# Røde Kors Roskilde – Hjemmesidedokumentation

Velkommen til GitHub-repositoriet for Røde Kors Roskildes WordPress-løsning.

## 🚀 Hurtig start
- **Hjemmeside:** [rodekors.dk/roskilde](https://...)
- **Staging / Testmiljø:** [test.rodekors-roskilde.dk](https://...)
- **WP Admin Login:** `/wp-admin`

## 📚 Hvor finder du hvad?
- **[Wiki](../../wiki):** Procesbeskrivelser, retningslinjer, kontaktpersoner og arbejdsgange.
- **[Docs-mappen](./docs/):** Layoutaftaler og tekniske manualer.
- **[Custom Tools](./custom-tools/):** Kildekode til vores egne plugins og tilpasninger.

## 🔒 Passwords og Adgangskoder
*Bemærk: passwords og følsomme koder gemmes EKSKLUSIVT i vores delte Bitwarden/1Password og må ikke lægges direkte i dette repository.*
```

---

## 2. Struktur til GitHub Wiki

Mens koden og de direkte guider ligger i mapperne, fungerer **Wikien** som et levende opslagsværk til hverdagsbrug, procesbeskrivelser og aftaler.

### Forside (Home)
Opret en klar forside på Wikien, der giver et hurtigt overblik over indholdet:

```markdown
# Røde Kors Roskilde Web - Wiki

Velkommen til holdets arbejds-wiki. Her samler vi alle aftaler, rutiner og overordnede informationer om webstedets drift.

### Hurtig navigation
1. [[Processer og Arbejdsgange]]
2. [[Design og Layoutaftaler]]
3. [[Servere, Domæner og Systemer]]
4. [[Dine Egne Tools / Plugins]]
5. [[Sikkerhed og Rettigheder]]
```

---

### Sideoversigt i Wikien

Når I opretter sider i Wikien (Sidebar menuen til højre opdateres automatisk), kan I strukturere dem således:

#### 🟢 Page 1: `Processer og Arbejdsgange`
* **Nyt indhold:** Hvordan godkendes og udgives nyheder/events?
* **Rollefordeling:** Hvem har ansvaret for hvad i teamet (tekst, billeder, teknik)?
* **Kvartalsvise tjek:** Opdatering af WordPress, kontrol af døde links, oprydning i brugere.

#### 🔵 Page 2: `Design og Layoutaftaler`
* **Visuel identitet:** Røde Kors' officielle farvekoder (Primary Red `#EE2A24` osv.) og skrifttyper.
* **Billedstandarder:** Anbefalede dimensioner (f.eks. `1200x630px` til herobilleder) og komprimering inden upload.
* **Komponenter:** Standardblokke i Gutenberg/Wordpress (f.eks. hvornår bruges opfordringsknapper, fremhævede bokse osv.).

#### 🟡 Page 3: `Servere, Domæner og Systemer`
* **Adresser:** URL'er til prod, staging, DNS-udbyder og webhosting-kontrolpanel.
* **Tredjepartstjenester:** Integrationer til evt. nyhedsbrev, formularer, Google Analytics/Matomo.
* **Password-procedure:** Hvor og hvordan deles adgangskoder sikkert i teamet.

#### 🔴 Page 4: `Egne Tools og Custom Kode`
* **Oversigt:** Kort forklaring af de specielle værktøjer du har bygget (hvad de gør, og hvorfor WordPress ikke klarede det standard).
* **Brugermanual:** Hvordan de andre 3–4 personer aktiverer, indstiller eller tilpasser dine værktøjer.
* **Vedligeholdelse:** Noter om opdateringer eller afhængigheder.

---

### Gode råd til udformningen
* **Brug skabeloner:** Lav en standard for, hvordan en guide skal se ud (Titel $\rightarrow$ Formål $\rightarrow$ Step-by-step procedure).
* **Gem kodestumper i Git, henvis fra Wiki:** Skriv den dybe forklaring i Wikien, men henvis med et link til `.html`- eller `.php`-filerne i `/snippets/` eller `/custom-tools/`. Det gør det nemt at opdatere koden uden at ødelægge teksten.

<FollowUp label="Vil du have et eksempel på, hvordan en 'redaktør-guide' eller en 'custom code snippet' kan formateres i Markdown?" query="Vis et konkret eksempel på en Markdown-skabelon til en redaktør-guide eller en kodestump-dokumentation til GitHub."/>

---

# you asked

message time: 2026-08-09 18:05:23

Vis et konkret eksempel på en Markdown-skabelon til en redaktør-guide eller en kodestump-dokumentation til GitHub.

---

# gemini response

Her er to konkrete eksempler på Markdown-skabeloner, som du enten kan lægge direkte i din `/docs/`-mappe eller indsætte på en GitHub Wiki-side.

---

### Eksempel 1: Redaktør-guide (Proceduredokumentation)

```markdown
# Redaktørguide: Oprettelse af begivenheder og arrangementer

Denne guide beskriver workflowet for oprettelse og publicering af nye arrangementer på Røde Kors Roskildes hjemmeside.

---

## 📋 Tjekliste før publicering
- [ ] Billeder er skaleret til **1200x630 px** og komprimeret (max 200 KB).
- [ ] Dato, tid og adresse er verificeret af aktivitetslederen.
- [ ] Eventuel tilmeldingsfrist eller eksternt link er testet.

---

## 🛠 Step-by-step arbejdsgang

### 1. Opret nyt arrangement
1. Log ind i WordPress admin på `/wp-admin`.
2. Gå til **Arrangementer** $\rightarrow$ **Tilføj nyt** i venstremenuen.
3. Indtast arrangementets titel (f.eks. *Værestedets Sommerfest 2026*).

### 2. Formatering af indhold
* **Overskrift 2 (H2):** Bruges til hovedafsnit (f.eks. *Program*, *Praktisk information*).
* **Fremhævet boks:** Tilføj blokken **Røde Kors Callout** til vigtige beskeder som tilmeldingsfrister.

### 3. Billeder og Kategori
1. Vælg den relevante kategori under **Aktiviteter** i højre sidebjælke (f.eks. *Nørklere*, *Genbrug*, *Socialt arbejde*).
2. Sæt **Udvalgt billede** (Featured Image). Remember altid at udfylde **ALT-tekst** for tilgængelighed.

---

## ⚠️ Vigtige regler for Røde Kors visuel identitet
> **Bemærk:** Vi bruger altid den officielle Røde Kors rød (`#EE2A24`) til knapper og fremhævelser. Undgå at ændre tekstfarver manuelt i brødteksten.

---

## 👤 Kontaktperson
Har du spørgsmål til denne guide, kan du kontakte web-ansvarlig i GitHub-issue eller direkte på Slack/Teams.
```

---

### Eksempel 2: Kodestump / Custom Værktøj (Teknisk dokumentation)

```markdown
# Værktøj: Genbrugsbutik Åbningstider (Custom PHP Snippet)

Dette modul genererer en dynamisk visning af butikkens åbningstider og helligdags-status via en WordPress shortcode.

---

## 🛠 Placering i projektet
* **Filplacering:** `/snippets/opening-hours-widget.php`
* **Type:** Custom PHP / Shortcode
* **Afhængigheder:** WordPress 6.0+, PHP 8.1+

---

## 🚀 Anvendelse

Sæt følgende shortcode ind i en vilkårlig Gutenberg-blok eller side:

```text
[rodekors_aabningstider butik="roskilde-centrum"]
```

### Parametre
| Parameter | Type | Standard | Beskrivelse |
| :--- | :--- | :--- | :--- |
| `butik` | String | `roskilde-centrum` | Slug for den specifikke afdeling/butik. |
| `show_holidays` | Boolean | `true` | Viser om butikken har ekstraordinært lukket på helligdage. |

---

## 💻 Kildekode (Uddrag)

```php
<?php
/**
 * Shortcode handler for Røde Kors Åbningstider
 */
function rkr_render_opening_hours( $atts ) {
    $a = shortcode_atts( array(
        'butik' => 'roskilde-centrum',
        'show_holidays' => 'true',
    ), $atts );

    $output = '<div class="rkr-opening-hours">';
    // Logik til at hente åbningstider
    $output .= '<h3>Åbningstider</h3>';
    $output .= '</div>';

    return $output;
}
add_shortcode( 'rodekors_aabningstider', 'rkr_render_opening_hours' );
```

---

## 🔄 Opdatering og Vedligeholdelse
1. Test altid ændringer på **Staging-miljøet** før koden lægges i `functions.php` eller i plugin'et på live-sitet.
2. Hvis der tilføjes nye parametre, skal skemaet ovenfor opdateres i dette dokument.
```

<FollowUp label="Vil du have hjælp til at skrive en .gitignore-fil til jeres WordPress-setup?" query="Vis et eksempel på en .gitignore-fil til et WordPress-projekt med custom plugins og dokumentation på GitHub."/>

---

# you asked

message time: 2026-08-09 18:16:50

Tak det er fantastisk. Jeg har et lignende projekt kørende i den lokalhistoriske forening Syd for Banen. Her er vi to der laver en Wordpress portal. Vo er henholdsvis 80 og 78 å gamle. Derfor et det på tide at vi kommer i gang med dokumentationen - helt som med Røde Kors. Vil du lave noget lignende så jeg kan komme i gang i Github med SFB portalen.

---

# gemini response

Selvfølgelig! Hvor er det et flot og vigtigt initiativ – især når man skal sikre, at alt det lokalhistoriske arbejde, I opbygger, nemt kan overlades til nye kræfter med tiden.

Syd for Banen (SFB) har et særligt præg med lokalhistoriske arkiver, artikler, interaktive kort, lyd/podcasts, billedsamlinger og data (som f.eks. jeres registreringer af butikker og adresser).

Her er et skræddersyet forslag til **mappestruktur** og **Wiki-opbygning** til et privat GitHub-repository specifikt for **Syd for Banen-portalen**.

---

## 1. Mappestruktur i repositoriet (`sfb-portal-docs`)

I selve repositoriet samles kildekoder, datastrukturer, skabeloner og de mest centrale tekniske guider.

```text
sfb-portal/
├── .github/
│   └── CODEOWNERS               # Overblik over hvem der har ansvaret
├── custom-tools/                # Custom plugins, PHP-moduler og kort-scripts
│   ├── sfb-kort-integration/    # Scripts til interaktive kort og geokoder
│   └── sfb-audio-player/        # Custom lyd/podcast-komponenter
├── data-templates/              # Skabeloner til historisk dataindsamling
│   ├── adresser-og-butikker.json # Eksempel/skabelon på adresseregistrering
│   └── metadata-schema.md       # Hvordan historiske data (tags, perioder) struktureredes
├── docs/                        # Guider og tekniske manualer
│   ├── arkivering-og-media.md   # Retningslinjer for lyd, billeder og flipbooks
│   └── wordpress-setup.md       # Temaer, plugins og serverkonfiguration
├── snippets/                    # HTML-, CSS- og PHP-kodestumper til genbrug
│   ├── artikel-skabelon.html
│   └── kort-embed.html
├── .gitignore                   # Filer Git skal se bort fra (f.eks. store mediefiler/WP-koder)
└── README.md                    # Repositoriets hovedside
```

### Hoved-`README.md` (Repositoriets forside)

```markdown
# Syd for Banen (SFB) – Portal & Dokumentation

Velkommen til GitHub-repositoriet for Syd for Banen-portalens digitale ressourcer. 
Dette repository bruges til dokumentation af teknik, arbejdsgange og data, så portalen kan drives og videreudvikles sikkert.

## 📌 Hurtige genveje
- **Offentlig portal:** [sfbbilleder.eu/port](http://sfbbilleder.eu/port) (eller jeres primære domæne)
- **WordPress Admin:** `/wp-admin`
- **[Syd for Banen Wiki](../../wiki):** Vores primære opslagsværk med arbejdsgange, indholdskategorier og historiske datastandarder.

## 🗂 Hvad finder du her?
- `/custom-tools/`: Kildekode til specialudviklede visninger, kort eller plugins.
- `/data-templates/`: Skabeloner til registrering af adresser, erhverv, perioder og tag-strukturer.
- `/docs/`: Manualer for billedbehandling, lydredigering/podcasts og PDF/Flipbook-udgivelse.

## 🔒 Passwords og Adgangskoder
Adgangskoder til hosting, DNS og WordPress gemmes **aldrig** direkte i koden her. Kontakt den ansvarlige for adgang til vores delte adgangskodesystem.
```

---

## 2. Struktur til GitHub Wiki (SFB Portal)

Wikien fungerer som jeres overskuelige "håndbog" for hverdagens arbejde og digitaliseringen.

### Forside (`Home.md`)

```markdown
# Syd for Banen Portal – Digital Håndbog

Denne wiki indeholder alle aftaler, rutiner og retningslinjer for digitaliseringen og portalen for *Syd for Banen*.

### Quick Navigation
1. [[01. Redaktion & Arbejdsgange]]
2. [[02. Registrering af Historisk Data]]
3. [[03. Lyd, Podcasts og Flipbooks]]
4. [[04. Interaktive Kort og Geokodning]]
5. [[05. WordPress Setup & Custom Kode]]
6. [[06. Hosting, Domæner og Sikkerhed]]
```

---

### Indholdsoversigt for Wiki-siderne

#### 📄 Page 1: `01. Redaktion & Arbejdsgange`
* **Nye artikler og portrætter:** Processen fra idé/interview til publiceret artikel.
* **Kategorier & Tags:** Fastlagt struktur (f.eks. *Portrætter og Samtaler*, *Kultur og Projekter*, *Byudvikling* m.fl.).
* **Kildangivelse & Ophavsret:** Regler for brug af historiske billeder (Roskilde Lokalhistoriske Arkiv, private donationer m.m.).

#### 📄 Page 2: `02. Registrering af Historisk Data`
* **Format for butikker/adresser:** Hvordan vi strukturerer oplysninger om veje, husnumre, periode-start/slut og beskrivelse.
* **Brug af tags:** Standarder for tags (f.eks. `#Købmand`, `#Frisør`, `#Køgevej`, `#Sydbyen`).
* **Kvalitetskontrol:** Tjekliste for at sikre, at koordinater og årstal er korrekte, før data importeres/vises.

#### 📄 Page 3: `03. Lyd, Podcasts og Flipbooks`
* **Lydfiler & Podcasts:** Format (MP3), varighed, upload-procedure samt integration med Spotify/Podcast-afspillere.
* **Bøger & Flipbooks:** Hvordan print-materialer/bøger laves om til digitale bladre-bøger (Flipbooks) eller PDF-ressourcer.
* **Billedoptimering:** Standardstørrelser på kort- og artikelbilleder så siden indlæses hurtigt.

#### 📄 Page 4: `04. Interaktive Kort og Geokodning`
* **Kortmodul:** Hvordan kortvisningen på portalen hender koordinater (`latitude, longitude`).
* **Nye punkter:** Guide til at finde koordinater og koble dem til historiske fortællinger eller butikker.

#### 📄 Page 5: `05. WordPress Setup & Custom Kode`
* **Brugte Plugins:** Liste over essentielle plugins og hvad de gør (f.eks. Print My Blog, afspillere, kort-plugins).
* **Dine custom tools:** Dokumentation af de specialudviklede værktøjer/scripts, du har skrevet til portalen.

---

### 💡 Gode råd til at komme i gang

1. **Opret repositoriet som `Private`** på GitHub (f.eks. `sfb-portal-docs`).
2. **Invitér din makker** under **Settings $\rightarrow$ Collaborators** via hans e-mail eller GitHub-brugernavn.
3. **Start i Wikien:** Begynd med at oprette siderne for `01. Redaktion & Arbejdsgange` og `02. Registrering af Historisk Data`. Det giver hurtigt værdi, selv før I har lagt megen kode ind.
4. **Link til filer:** Når du har kodestumper eller JSON-skabeloner i repositoriet, kan du fra Wikien blot henvise med et direkte link ned i mapperne.

<FollowUp label="Vil du have et skabelon-eksempel på en Wiki-side til registrering af historisk data eller lyd/podcasts?" query="Vis en skabelon til en Wiki-side om registrering af historiske data og lyd/podcasts til SFB-portalen."/>

---

# you asked

message time: 2026-08-09 18:17:23

Vis en skabelon til en Wiki-side om registrering af historiske data og lyd/podcasts til SFB-portalen.

---

# gemini response

Her er en konkret Markdown-skabelon til en GitHub Wiki-side, som I direkte kan kopiere og tilpasse i Wikien på repositoriet for **Syd for Banen (SFB)**.

Skabelonen dækker både **datastrukturen** for historiske registreringer (som jeres "Glemte Butikker")  og **retningslinjerne for lyd og podcasts** (som jeres interviews, podwalks og Spotify-integrationer).

---

```markdown
# Wiki: Guideline for Registrering af Historiske Data og Podcasts

Denne side beskriver standarderne for oprettelse, strukturering og kvalitetssikring af historiske registreringer samt lyd- og podcastindhold på SFB-portalen.

---

## 1. Registrering af Historiske Data (f.eks. Glemte Butikker og Adresser)

For at kort, søgefunktioner og chatboten "Fortidsvennen" fungerer optimalt, skal alle registreringer følge den faste datastruktur.

### 📋 JSON-datastruktur (Skabelon)
Når der tilføjes nye butikker, erhverv eller historiske lokationer i dataarkivet (`data.json`), benyttes følgende felter:

```json
{
  "id": 1757428635,
  "navn": "Bakkegårdens Bager",
  "beskrivelse": "Bagerforretning i butikscentret på Køgevej lige ved Bakkegården. Det startede med Bager Damgård.",
  "tags": "#Bager, #Køgevej, #Bakkegården",
  "vej": "Køgevej",
  "husnr": "39",
  "postnr_by": "4000 Roskilde",
  "koordinater": "55.632066, 12.090251",
  "koordinat_ca": false,
  "periode_start": "1957",
  "periode_slut": "",
  "billede_url": "[https://sfbbilleder.eu/upload/eksempel.jpg](https://sfbbilleder.eu/upload/eksempel.jpg)",
  "mere_info_url": "[https://www.bakkegaardensbageri.dk/](https://www.bakkegaardensbageri.dk/)"
}
```

### 📌 Feltforklaring og Retningslinjer

1. **`id`**: Et unikt tal (genereres automatisk eller via tidsstempel).
2. **`navn`**: Butikkens/stedets navn i folkemunde eller historiske fagregistre.
3. **`beskrivelse`**: Kort tekst, der opsummerer erindringer, historiske facts eller særlige kendetegn.
4. **`tags`**: Hashtags adskilt af komma. Brug altid standardiserede tags (f.eks. `#Købmand`, `#Bager`, `#Køgevej`, `#Sydbyen`).
5. **`koordinater`**: Format: `breddegrad, længdegrad` (f.eks. `55.632066, 12.090306`).
   * Sæt `"koordinat_ca": true`, hvis den præcise adresse eller husnummer er usikkert.
6. **`periode_start` / `periode_slut`**: Årstal for forretningens eksistens. Efterlades blank (`""`), hvis slutåret er ukendt eller forretningen stadig findes.

---

## 2. Publicering af Lyd, Podcasts og Podwalks

SFB-portalen indeholder mange optagelser – fra interviews med lokale personligheder til podwalks om historiske områder (f.eks. Sankt Hans og Stituren).

### 🎙 Lydformat og Klargøring
* **Filformat:** MP3, 128 kbps (mono eller stereo).
* **Titel-konvention:** `SFB_Podcast_[Nummer]_[Emne/Navn].mp3` (f.eks. `SFB_Podcast_02_JoyMogensen.mp3`).
* **Varighed:** Varigheden (f.eks. `40:32` min.) angives i indlæggets introduktion.

### 📄 WordPress-Publicering af Podcasts

Når et nyt lydafsnit oprettes i WordPress som et indlæg:

1. **Kategori:** Vælg *Portrætter og Samtaler*, *Kultur og Projekter* eller *Bydel og Infrastruktur*.
2. **Tags:** Tilføj altid relevante tags samt tagget `Podcast` (og evt. `Podwalk` eller `Samtale`).
3. **Spotify / Afspiller-embed:** * Indsæt Spotify-iFrame eller den lokale HTML5-lydafspiller øverst i artiklen.
4. **Relateret Billedgalleri:**
   * Link direkte til det tilsvarende billedalbum på `sfbbilleder.eu`, så lytteren kan se relevante fotos, mens de lytter.
5. **Resumé & Transskription:**
   * Skriv altid et kort resumé af samtalen samt tidsstempler/emneopdeling, hvis optagelsen er lang.

---

## 🛠 Tjekliste før publicering på Portalen

- [ ] Er koordinaterne testet på det interaktive kort?
- [ ] Er billeder optimeret og placeret i webgalleriet (`sfbbilleder.eu`)?
- [ ] Indgår der lyd eller podcast, som er testet på både mobil og pc?
- [ ] Er relevante personnavne og gadenavne føjet til tags?
- [ ] Er der oprettet et GitHub-issue, hvis der opstår tekniske fejl på siden?

---
*Sidst opdateret: Februar 2026 af [Dit Navn / Poul Erik]*
```

---

### Sådan tager I det i brug i GitHub:
1. Gå ind på dit GitHub repository og klik på fanebladet **Wiki**.
2. Klik på **Add Page** eller **Edit** på en eksisterende side.
3. Indsæt koden ovenfor og klik **Save Page**.

---
Powered by [AI Exporter](https://saveai.net)
