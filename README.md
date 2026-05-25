# 4x4 Intervalltrening – PWA

Treningsapp for 4x4 intervallløping med pulsmåler (Polar), VO2maks-beregning og treningshistorikk.

---

## Installasjon

### 1. Host filene (Netlify Drop – enklest)
1. Gå til https://app.netlify.com/drop
2. Dra hele denne mappen inn i nettleseren
3. Du får en URL som f.eks. `https://amazing-name-123.netlify.app`

### 2. Installer på telefon
**Android (Chrome):**
- Åpne URL-en i Chrome
- Trykk på "Installer"-banneret som dukker opp, eller ⋮ → "Legg til på startskjerm"

**iPhone (Safari):**
- Åpne URL-en i Safari
- Trykk delingsikonet → "Legg til på hjemskjerm"

---

## Google Drive-synkronisering (valgfritt)

For å aktivere sky-synkronisering trenger du et Google OAuth 2.0 Client ID.
Dette er gratis og tar ca. 5 minutter å sette opp.

### Steg 1 – Opprett Google Cloud-prosjekt
1. Gå til https://console.cloud.google.com
2. Klikk "Select a project" → "New Project"
3. Gi det et navn, f.eks. "4x4 Trening", og klikk "Create"

### Steg 2 – Aktiver Google Drive API
1. Gå til "APIs & Services" → "Library"
2. Søk etter "Google Drive API" og klikk "Enable"

### Steg 3 – Opprett OAuth-legitimasjon
1. Gå til "APIs & Services" → "Credentials"
2. Klikk "Create Credentials" → "OAuth client ID"
3. Velg "Web application"
4. Under "Authorized JavaScript origins", legg til din Netlify-URL
   (f.eks. `https://amazing-name-123.netlify.app`)
5. Klikk "Create"
6. Kopier **Client ID** (ser slik ut: `123456789-abc...apps.googleusercontent.com`)

### Steg 4 – Lim inn Client ID i appen
1. Åpne `index.html` i en teksteditor
2. Finn denne linjen (ca. linje 510):
   ```
   const GDRIVE_CLIENT_ID='';
   ```
3. Lim inn Client ID:
   ```
   const GDRIVE_CLIENT_ID='123456789-abc...apps.googleusercontent.com';
   ```
4. Last opp den oppdaterte `index.html` til Netlify igjen

### Steg 5 – Konfigurer OAuth-samtykkeskjerm
1. Gå til "OAuth consent screen" i Google Cloud Console
2. Velg "External" → Fill
3. Fyll inn app-navn: "4x4 Trening"
4. Legg til din e-postadresse som testbruker

---

## Funksjoner
- 4x4 intervalltimer med nedtelling
- Polar-pulsbelt via Web Bluetooth (Chrome/Android)
- Hastighetsinnstillinger for tredemølle
- VO2maks-beregning med alderssammenligning
- Pulssoner og grafer
- Treningshistorikk med progresjon over tid
- Offline-støtte (Service Worker)
- Google Drive-synkronisering
- Eksport/import av treningsdata (JSON)

---

## Teknisk
- Ren HTML/CSS/JS – ingen byggeprosess nødvendig
- Chart.js for grafer
- Web Bluetooth API for Polar-tilkobling
- Google Drive REST API (appdata-scope)
- localStorage for lokal lagring
