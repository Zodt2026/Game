# Game-Design-Dokument (Entwurf v0.1)

> Lebendes Dokument – wird mit jeder Entscheidung aktualisiert.
> Arbeitstitel: **„Runenfall“** (Vorschlag, noch offen)

## 1. Vision in einem Satz

Ein stilisiert-düsteres Action-RPG (Isometrie, Klicksteuerung + Tastatur/Controller) mit **Magier und Bogenschützin**, in dem man sich über **Skill-Runen, Element-Reaktionen und fair balancierte Sets** eigene Builds zusammenbaut.

## 2. Säulen (daran messen wir jede Entscheidung)

1. **Builds basteln macht Spaß** – jede Entscheidung im Skillsystem spürt man im Kampf.
2. **Loot ist spannend, aber fair** – Sets und Legendaries verändern den Spielstil, nicht nur Zahlen.
3. **Kampf fühlt sich knackig an** – Treffer-Feedback, Effekte, Sound, flüssig auch auf schwacher Hardware.
4. **Klein, aber poliert** – lieber 2 Klassen richtig gut als 6 halbgar.

## 3. Klassen

| | **Magier** | **Bogenschützin** |
|---|---|---|
| Spielgefühl | Flächenschaden, Kontrolle, verwundbar | Mobil, Einzelziel-stark, Fallen |
| Ressource | Mana (regeneriert langsam) | Fokus (baut sich durch Treffer auf) |
| Schulen | 🔥 Feuer · ❄️ Frost · 🔮 Arkan | 🎯 Präzision · 🌿 Natur/Gift · 🌑 Schatten |

Pro Klasse ca. **12–15 aktive Skills** (4–5 pro Schule) + 1 Bewegungsskill.
Reihenfolge der Umsetzung: **erst Magier komplett**, dann Bogenschützin.

## 4. Skillsystem – drei Ebenen

### 4.1 Aktive Skills
- 6 Slots auf der Leiste (Maus links/rechts + 1–4 bzw. Controller-Tasten).
- Skills steigen durch Benutzung **nicht** auf – Stärke kommt aus Runen, Baum und Ausrüstung (vermeidet „Grind-Zwang“ beim Umbauen von Builds).
- Jederzeit kostenlos umbaubar → Experimentieren wird belohnt.

### 4.2 Skill-Runen (das Herzstück)
Jeder aktive Skill hat **3 Runen-Sockel**. Runen sind **Loot** und klassenübergreifend.

Beispiele:
| Rune | Wirkung |
|---|---|
| Spaltung | Projektil teilt sich beim Treffer in 3 |
| Echo | Skill wird nach 1 s mit 50 % Schaden wiederholt |
| Wandlung: Frost | Schaden wird zu Frostschaden |
| Kettenreaktion | Getötete Gegner explodieren |
| Ruhe | +40 % Schaden, aber +30 % Abklingzeit |

→ Ein Feuerball mit *Spaltung + Echo + Wandlung: Frost* spielt sich völlig anders als ein reiner Feuerball.
Regeln gegen Missbrauch: Runen haben **Tags** (Projektil, Fläche, Kanalisiert …) und passen nur auf Skills mit passenden Tags; manche Runen schließen sich gegenseitig aus.

### 4.3 Passiver Baum „Sternbild“
- Pro Klasse ein Baum mit ca. **80–100 Knoten**, 1 Punkt pro Level + Bonuspunkte aus Quests.
- Kleine Knoten (+Werte), mittlere Knoten (spürbare Effekte), **Schlüsselsteine** (regelverändernd, z. B. „Mana-Schild: Schaden geht zuerst auf Mana“).
- Kostenlos zurücksetzbar in der Stadt (Experimentieren > Bestrafen).

### 4.4 Element-Reaktionen (unser Alleinstellungsmerkmal)
Skills hinterlassen **Zustände** auf Gegnern. Trifft ein zweites Element, entsteht eine **Reaktion**:

| Zustand + Treffer | Reaktion |
|---|---|
| Brennend + Frost | **Dampfexplosion** – Flächenschaden + Blenden |
| Unterkühlt + Arkan | **Zersplittern** – kritischer Bonusschaden |
| Vergiftet + Feuer | **Giftwolke** – Gift breitet sich aus |
| Markiert (Präzision) + Schatten | **Hinrichtung** – sofortiger Bonusschaden unter 30 % Leben |

So entstehen Kombos *innerhalb einer Klasse* und später im **Koop** (Magier legt Frost, Bogenschützin zündet).

## 5. Ausrüstung & Loot

### 5.1 Seltenheitsstufen
Normal → Magisch (1–2 Affixe) → Selten (3–5 Affixe) → **Legendär** (1 einzigartiger Effekt) → **Set**

### 5.2 Affixe
- Jedes Affix hat **Stufen (Tiers)**, abhängig vom Gegenstandslevel.
- **Power-Budget**: jeder Gegenstand hat ein festes Budget (abhängig von Level + Seltenheit); Affixe „kosten“ Budget. Das ist die Grundlage für saubere Balance.

### 5.3 Sets – balanciert statt übermächtig
Lehre aus anderen Spielen: Sets mit riesigen Multiplikatoren machen alles andere wertlos. Unsere Regeln:
1. **Set-Boni verändern den Spielstil**, Zahlenboni sind moderat (2er-Bonus ≈ Wert eines guten Affixes, 4er-Bonus ≈ ein Schlüsselstein).
2. Set-Teile haben **weniger Affix-Budget** als Seltene – der Bonus *ersetzt* Werte, er kommt nicht obendrauf.
3. Jedes Set unterstützt einen **Build-Archetyp**, keinen einzelnen Skill (mehrere Wege bleiben offen).
4. Sets sind **nicht Pflicht**: Ein gut gerollter Seltener + Legendär muss konkurrenzfähig sein (Ziel: ±10 % DPS).
5. Sets droppen auf allen Stufen und skalieren mit dem Gegenstandslevel.

Beispiel-Set Magier – **„Gewand des Frostfeuers“** (4 Teile)
- 2 Teile: Brennende Gegner erhalten 15 % mehr Frostschaden.
- 4 Teile: Dampfexplosionen hinterlassen eine Eiswolke, die 3 s lang Gegner verlangsamt und erneut Reaktionen auslösen kann.

### 5.4 Balancing-Werkzeug
Alle Werte (Skills, Affixe, Sets, Gegner) liegen **datengetrieben** in Tabellen/ScriptableObjects.
Zusätzlich bauen wir ein **Simulations-Skript**, das DPS und Überlebensfähigkeit vieler Build-Kombinationen automatisch durchrechnet und Ausreißer meldet.

## 6. Spielwelt & Struktur

- Stilisierte Dark-Fantasy, handgemalter/Low-Poly-Look, warme Lichtquellen in düsteren Umgebungen.
- **3 Akte** mit je einer Stadt und 3–4 Gebieten (teilweise prozedural zusammengesetzt), Bossen am Ende.
- Kurze Story, die nicht im Weg steht.
- **Endgame**: „Risse“ – endlose Dungeons mit Stufen und zufälligen Modifikatoren, Bestenliste über Steam.

## 7. Technik

- **Unity 6, URP**, Ziel: 60 FPS auf integrierter Grafik (Intel UHD 630) bei mittleren Einstellungen.
- Steuerung: Maus + Tastatur, Controller (Steam Deck!).
- Steam: Erfolge, Cloud-Speicher, Bestenlisten (via Steamworks.NET).
- Code-Architektur: datengetrieben (ScriptableObjects), Kampf über ein zentrales Schadens-/Status-System, damit Runen, Reaktionen und Sets sauber zusammenspielen.
- Assets: zugekaufte Packs (Umgebung, Charaktere, Effekte) im einheitlichen Stil.

## 8. Meilensteine

| # | Meilenstein | Inhalt |
|---|---|---|
| M0 | Grundgerüst | Unity-Projekt, Repo, Ordnerstruktur ✅ (teilweise) |
| M1 | **Bewegung & Kampf** | Isometrische Kamera, Klick-Bewegung, 1 Gegner-Typ, Feuerball, Leben/Mana, Schadenszahlen |
| M2 | Skills & Runen | 4 Magier-Skills, Runen-Sockel, erste Element-Reaktion |
| M3 | Loot | Drops, Affixe, Inventar, Ausrüstung, erstes Set |
| M4 | Fortschritt | Level, Sternbild-Baum, Speichern/Laden |
| M5 | Vertical Slice | 1 Gebiet + Boss in „echter“ Optik → **Steam-Seite + Wunschliste starten** |
| M6 | Bogenschützin | zweite Klasse |
| M7 | Inhalt | Akte 1–3, Endgame „Risse“ |
| M8 | Early Access / Release | Steam-Integration, Feinschliff, Marketing |

## 9. Offene Fragen

- Arbeitstitel?
- Koop-Multiplayer ja/nein? (stark für Verkäufe, aber deutlich mehr Aufwand → frühestens nach M5 entscheiden; Architektur halten wir offen)
- Preisrahmen (vermutlich 15–20 €)?
