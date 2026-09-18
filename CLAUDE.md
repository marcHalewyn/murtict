# Werkafspraken voor deze repo

Statische one-pager. Geen build-stap, geen framework, geen package manager.
Wijzigingen zijn dus altijd directe bewerkingen in HTML of CSS.

## Harde regels

- **Geen externe verzoeken toevoegen.** Geen Google Fonts, geen CDN's, geen analytics,
  geen embedded widgets. De site laadt nu uitsluitend eigen bestanden en dat is bewust:
  het scheelt laadtijd en voorkomt dat bezoekersgegevens naar derden gaan.
- **Geen cookies, geen tracking, geen contactformulier.** Zodra een van die drie erin komt,
  moet de privacyverklaring mee worden aangepast en is er mogelijk een cookiebanner nodig.
- **Geen build-tooling introduceren** zonder dat daar een aanleiding voor is. De site moet
  te onderhouden blijven door iemand die alleen HTML kent.
- Kleuren komen uit de CSS-variabelen bovenaan `css/style.css`. Geen losse hex-waarden
  in de HTML bijzetten.

## Let op bij wijzigingen: waar staat wat

Een paar gegevens staan op meerdere plekken. Wijzig je er één, controleer dan de rest.

**Telefoonnummer (06 14 958 768)** staat op zes plekken:
1. `index.html` — header, zichtbare tekst
2. `index.html` — header, `href="tel:+31614958768"`
3. `index.html` — hero-knop (tekst én `tel:`-link)
4. `index.html` — contactsectie-knop (tekst én `tel:`-link)
5. `index.html` — footer, en in de JSON-LD onderaan (`telephone`)
6. `privacy.html` en `404.html`
Plus: de WhatsApp-links gebruiken `https://wa.me/31614958768`.
Plus: **het nummer is ingebrand in `assets/og-image.jpg`** — die afbeelding moet opnieuw
gegenereerd worden als het nummer verandert.

**Werkgebied (Utrecht, Vleuten, Maarssen, Harmelen, Woerden, Montfoort)** staat op twee plekken:
de sectie `#werkgebied`, de contactsectie, én `areaServed` in de JSON-LD.

**Bedrijfsnaam** staat in de header, de footer, de `<title>`, de meta-description,
de Open Graph-tags, de JSON-LD (`name`) en in `assets/og-image.jpg`.

**KvK-nummer 77480570** staat in de footer van `index.html` en in `privacy.html`.

## Feitelijke gegevens

Verzin hier niets bij. Deze gegevens komen van de klant en staan vast:

- Bedrijf: Laptop en Computer Reparatie, voorheen Laptop en Computer Hulp
- Actief sinds 2010, KvK 77480570
- Telefoon en WhatsApp: 06 14 958 768
- Werkt op afspraak, maar is 24/7 telefonisch bereikbaar
- Geen fysieke inloopvestiging; geen adres op de site
- Gratis en vrijblijvend onderzoek, analyse en advies binnen 24 uur
- Alle merken, ook Apple

Nieuwe claims over prijzen, garantietermijnen, levertijden of certificeringen mogen er
alleen in als de klant ze bevestigd heeft.

## Werkwijze

`main` is wat live staat. Elke wijziging gaat via een korte branch met een PR: Netlify maakt
daar automatisch een deploy preview van, zodat je de wijziging op een echte URL kunt bekijken
voordat hij live gaat. Na merge naar `main` deployt Netlify vanzelf.

## Controleren voor je merget

- Bekijk de deploy preview op telefoonbreedte, niet alleen op desktop
- Geen horizontale scroll op 390px breed
- Tekstkleur op achtergrond moet minimaal 4,5:1 contrast houden
- `tel:`- en `wa.me`-links werken en bevatten het juiste nummer
