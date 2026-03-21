# 🥛 Kefir Dashboard

Interaktive Web-App zum Tracken und Simulieren der Kefir-Fermentation.

## Features

- **🧪 Fermentations-Simulator** – Schieberegler für Lagerort (Kühlschrank/Raumtemperatur), Lagerzeit und Milchfettgehalt mit Live-Visualisierung
- **📊 Echtzeit-Eigenschaften** – Säure, Kohlensäure, Dickflüssigkeit, Probiotika, Alkoholgehalt und Restlaktose werden dynamisch berechnet
- **📖 Wissen & Lagerung** – Umfassende Infos zur Knollen-Lagerung im Urlaub, Kefir-Herstellung, Gefahren und Empfehlungen
- **📝 Notizen-System** – Persönliche Erfahrungsberichte speichern, als Favoriten markieren, bearbeiten und löschen
- **☁️ Firebase Sync** – Alle Daten werden in Firebase gespeichert, Multi-User-fähig
- **📱 Responsive** – Funktioniert auf Desktop und Mobilgeräten

## Dateien

```
kefir-dashboard/
├── index.html      ← Gesamte App (Single-File)
├── kefir-icon.svg  ← App-Icon
└── README.md       ← Diese Datei
```

## Deployment auf GitHub Pages

### Schritt 1: Repository erstellen
1. Gehe zu [github.com/new](https://github.com/new)
2. Name: `kefir-dashboard` (oder beliebig)
3. Public wählen
4. "Create repository" klicken

### Schritt 2: Dateien hochladen
1. Auf der Repository-Seite "uploading an existing file" klicken
2. **Beide Dateien** (`index.html` und `kefir-icon.svg`) per Drag & Drop hochladen
3. "Commit changes" klicken

### Schritt 3: GitHub Pages aktivieren
1. Im Repository → **Settings** → **Pages** (linke Sidebar)
2. Source: **Deploy from a branch**
3. Branch: **main** | Ordner: **/ (root)**
4. "Save" klicken

### Schritt 4: Warten & Aufrufen
- GitHub braucht ca. 1-2 Minuten
- Deine App ist dann erreichbar unter: `https://DEIN-USERNAME.github.io/kefir-dashboard/`

## Firebase

Die App nutzt Firebase Firestore für:
- Speichern des letzten Slider-Zustands (pro User)
- Speichern der persönlichen Notizen
- Echtzeit-Synchronisation

Die Firebase-Config ist bereits in der `index.html` eingebettet.

### Firestore Security Rules (empfohlen)

Damit User nur ihre eigenen Daten lesen/schreiben können, setze in der Firebase Console unter Firestore → Rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /kefir_states/{userId} {
      allow read, write: if true;
    }
    match /kefir_notes/{noteId} {
      allow read, write: if true;
    }
  }
}
```

> ⚠️ Für Produktivbetrieb sollten strengere Rules verwendet werden (z.B. Auth-basiert).

## Technologien

- Vanilla HTML/CSS/JS (kein Framework nötig)
- Firebase Firestore (Echtzeit-Datenbank)
- Google Fonts (DM Serif Display + DM Sans)
- Responsive CSS Grid Layout

## Lizenz

Frei verwendbar für persönliche Zwecke.
