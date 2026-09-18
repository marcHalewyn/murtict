# laptopencomputerreparatie.nl

Statische one-pager voor Laptop en Computer Reparatie (voorheen Laptop en Computer Hulp),
laptop- en pc-reparatie in Utrecht en omgeving.

Geen build-stap, geen framework, geen externe verzoeken: puur HTML en CSS.

## Structuur

```
index.html          De volledige one-pager
privacy.html        Privacyverklaring
404.html            Foutpagina (Netlify serveert deze automatisch)
css/style.css       Alle styling, met de kleuren als CSS-variabelen bovenaan
assets/             Portretfoto, favicon, touch-icon, Open Graph-afbeelding
netlify.toml        Publicatie-instellingen, beveiligings- en cacheheaders
robots.txt          Zoekmachine-instructies
sitemap.xml         Sitemap (datums bijwerken bij grotere wijzigingen)
```

## Lokaal bekijken

De pagina gebruikt absolute paden (`/css/style.css`), dus openen via `file://` werkt niet goed.
Start een lokale server:

```bash
python -m http.server 8000
# open http://localhost:8000
```

## Tekst aanpassen

Alle teksten staan gewoon in `index.html`. Let op deze plekken bij wijzigingen:

- **Telefoonnummer** komt op vier plaatsen voor: de header, twee knoppen, en de footer.
  Ook in de JSON-LD onderaan (`telephone`) en in `assets/og-image.jpg`.
- **Werkgebied** staat in de sectie `#werkgebied` én in de JSON-LD (`areaServed`).
- **Bedrijfsnaam** staat in de header, de footer, de `<title>`, de Open Graph-tags en de JSON-LD.
- De **KvK-nummer** (77480570) staat in de footer en in `privacy.html`.

## Publiceren

De site draait op Netlify, gekoppeld aan deze repository: elke push naar `main` publiceert
automatisch. Er is geen build-commando; Netlify publiceert de map zoals die is.

### DNS bij TransIP

Het domein blijft bij TransIP staan. Bij de DNS-instellingen van het domein moet
**"TransIP-instellingen" op Uit** staan, anders overschrijft TransIP eigen records.
Daarna deze twee records (de exacte waarden staan in het Netlify-dashboard onder
Domain management — controleer ze daar voordat je ze doorgeeft):

| Naam | Type  | Waarde                     |
|------|-------|----------------------------|
| `@`  | A     | het IP dat Netlify toont   |
| `www`| CNAME | `<sitenaam>.netlify.app.`  |

Het HTTPS-certificaat wordt daarna automatisch door Netlify aangevraagd; er hoeft geen
SSL-certificaat gekocht te worden.

### Oude domeinen

De eerder gebruikte domeinen krijgen een 301-doorverwijzing naar
`https://laptopencomputerreparatie.nl/`, zodat bestaande vindbaarheid en de URL op oude
flyers blijven werken.

## Lettertypen

De site gebruikt de systeem-lettertypestack (Segoe UI op Windows, San Francisco op Apple,
Roboto op Android). Dat scheelt externe verzoeken, maakt de site sneller en voorkomt dat er
bezoekersgegevens naar Google Fonts gaan.

Wil je alsnog de lettertypen uit het oorspronkelijke ontwerp (Space Grotesk voor koppen,
Source Sans 3 voor lopende tekst): download de `.woff2`-bestanden, zet ze in `assets/fonts/`,
voeg `@font-face`-regels toe bovenaan `css/style.css` en pas `--font-head` en `--font-body` aan.
De rest van de styling hoeft niet te veranderen.

## Gecontroleerd

- Geen horizontale scroll op 390px breed
- Alle kleurcombinaties halen WCAG AA (laagste waarde 5,2:1)
- Geen console-fouten en geen mislukte verzoeken
- Geen cookies, geen tracking, geen externe verzoeken
