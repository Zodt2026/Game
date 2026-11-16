# Game (Arbeitstitel)

Ein Action-RPG im Stil von Diablo / Path of Exile, entwickelt mit **Unity 6 (URP)** für Steam.

## Einrichtung auf dem Mac (einmalig)

1. **GitHub Desktop** installieren: https://desktop.github.com
   - Mit GitHub anmelden und dieses Repository klonen, z. B. nach `~/Projekte/Game`.
   - Auf den Branch `claude/steam-game-development-s3k99o` wechseln.
2. **Unity Hub** installieren: https://unity.com/download
   - Kostenlosen Account anlegen, „Unity Personal“-Lizenz aktivieren.
   - Unter *Installs* die aktuelle **Unity 6 LTS** installieren.
   - Module zusätzlich anhaken: **Windows Build Support (Mono)** – damit wir vom Mac aus die Windows-Version für Steam bauen können.
3. **Projekt anlegen** (nur einmal, danach übernehme ich den Code):
   - Unity Hub → *New project* → Vorlage **Universal 3D** (URP).
   - Projektname: **`ARPG`**
   - Speicherort: der geklonte Repo-Ordner (z. B. `~/Projekte/Game`)
   - → Es entsteht `~/Projekte/Game/ARPG/`.
4. Unity einmal starten lassen, dann wieder schließen.
5. In GitHub Desktop alle neuen Dateien committen („Unity-Projekt angelegt“) und **Push** drücken.

Ab dann schreibe ich die Spielsysteme (C#-Skripte) und pushe sie; du holst sie per **Pull** in GitHub Desktop, öffnest Unity und testest.

## Hardware-Hinweis

Entwicklungsrechner: Mac mini 2018 (Intel, integrierte Grafik). Deshalb:
- **URP** statt HDRP, auf Performance optimierte Einstellungen.
- Look: „stilisiert-düster“ statt fotorealistisch – wirkt gut und läuft auch auf schwächerer Hardware.
- Optionales Upgrade später: eine externe Grafikkarte (eGPU) über Thunderbolt 3.
