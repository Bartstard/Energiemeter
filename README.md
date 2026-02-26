# ⚡ Energie Monitor

Een lokale webpagina die realtime energieverbruik visualiseert via de **HomeWizard P1 meter**, aangevuld met een weersvoorspelling en zongrafiek op basis van jouw locatie.

---

## 📋 Vereisten

### Hardware
- **HomeWizard P1 meter** — aangesloten op je digitale energiemeter

### Netwerk
- De webpagina en de HomeWizard P1 meter moeten op **hetzelfde lokale netwerk** zitten
- De pagina communiceert rechtstreeks met de lokale API van de meter — er is geen cloudverbinding nodig

### HomeWizard instelling
1. Open de **HomeWizard Energy app** op je smartphone
2. Ga naar de instellingen van je P1 meter
3. Activeer de optie **"Local API"**
4. Noteer het **IP-adres** van de meter (bv. `192.168.1.105`)

---

## 🚀 Installatie

1. Download `index.html` uit deze repository
2. Open het bestand in een webbrowser op een apparaat dat verbonden is met je lokale netwerk
3. Scroll naar beneden op de pagina
4. Vul bij **"🔌 IP-adres HomeWizard energiemeter"** het IP-adres van jouw P1 meter in
5. Klik op **Opslaan** — de pagina herverbindt meteen met de meter

Het IP-adres wordt opgeslagen in de lokale opslag van je browser zodat je het niet opnieuw hoeft in te vullen.

---

## 🌟 Functies

### Energieverbruik
- **Realtime gauge** — huidig vermogen in watt, vernieuwd elke seconde
- **Berekende kwartierpiek** — prognose van het piekvermogen voor het lopende kwartier
- **Kwartierpiek** — gemiddeld vermogen van het huidige kwartier
- **Maandpiek** — hoogste kwartierpiek van de lopende maand
- **Geïmporteerd / Geïnjecteerd / Netto verbruik** — totale energietellingen in kWh
- Achtergrondkleur reageert op het verbruik (groen / oranje / rood)

### Weersvoorspelling
- **Zongrafiek** — verwacht percentage zonneschijn per uur voor de komende 24 uur, inclusief neerslag en temperatuur
- **7-daagse weersvoorspelling** — met pictogrammen, temperatuur, neerslag, zonneschijnduur en stralingswaarde
- **Locatieselector** — zoek elke stad of gemeente; de keuze wordt opgeslagen
- Standaard ingesteld op **Mol, België**
- Weerdata via [Open-Meteo](https://open-meteo.com/) (gratis, geen API-sleutel nodig)

### Interface
- **Dark mode** — schakelbaar via knop rechtsboven, keuze wordt bewaard
- **Testmodus** — werkt met gesimuleerde data, uitsluitend handmatig te activeren
- **Automatische update check** — vergelijkt de lokale versie met de nieuwste versie op GitHub; toont een downloadknop als er een update beschikbaar is
- **Versienummer** — zichtbaar in de voetnoot, samen met de GitHub-versie

---

## ⚙️ Configuratie

Alle instellingen worden bewaard in de lokale opslag van de browser (`localStorage`) en blijven beschikbaar na het herladen van de pagina:

| Instelling | Omschrijving |
|---|---|
| IP-adres energiemeter | Lokaal IP van de HomeWizard P1 meter |
| Locatie weersvoorspelling | Stad of gemeente voor weerdata |
| Dark mode | Lichte of donkere weergave |

---

## 🔌 API

De pagina gebruikt de lokale REST API van de HomeWizard P1 meter:

```
GET http://<IP-ADRES>/api/v1/data
```

Gebruikte velden:
- `active_power_w` — huidig vermogen (W)
- `active_power_average_w` — gemiddeld vermogen huidig kwartier (W)
- `montly_power_peak_w` — maandpiek (W)
- `total_power_import_kwh` — totaal geïmporteerde energie (kWh)
- `total_power_export_kwh` — totaal geïnjecteerde energie (kWh)

Meer info: [HomeWizard API documentatie](https://api-documentation.homewizard.com/)

---

## 📦 Gebruikte technologieën

- [Plotly.js](https://plotly.com/javascript/) — gauge en grafieken
- [Open-Meteo API](https://open-meteo.com/) — weersverwachting
- [Nominatim / OpenStreetMap](https://nominatim.org/) — locatie zoeken
- [GitHub API](https://docs.github.com/en/rest) — update check

---

## 📄 Licentie

Vrij te gebruiken voor persoonlijk gebruik.
