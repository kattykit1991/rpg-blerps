# 🌱 PROJECT START

<!-- KAT · DEV TOOLS | Vorlagen-Release: v1.0.0 | 2026-11-03 -->

> Der kurze Startpunkt für DAS DING™.
> Hier wird geklärt, was ich bauen will, warum ich es bauen will und was für das aktuelle Ziel erstmal draußen bleibt.

---

## 💡 THE THING™

**Was baue ich?**

Ein rundenbasiertes C#-Konsolen-RPG namens **rpg-blerps**, inspiriert von meinem früheren Python-Abenteuer **„Der Frost in Ader 4-B“**.

Das Spiel ist in meiner Fantasy-Welt **Aeth'Veara** angesiedelt, genauer gesagt in Eklésia, im Handwerkerviertel „Die Unteren Tiegel“.

Die Spielergruppe tritt gegen Gegner wie Rost-Nager und defekte Scutter an.

Das Projekt verbindet eine überschaubare RPG-Kampfarena mit den Grundlagen objektorientierter Programmierung.

---

## ✨ WHY

**Warum will oder muss ich das bauen?**

Das Projekt ist eine freiwillige Übung im Rahmen meiner Software-Engineering-Weiterbildung bei der WBS CODING SCHOOL.

Ich möchte die Grundlagen der objektorientierten Programmierung in C# praktisch anwenden und besser verstehen:

- Klassen und Objekte
- Kapselung (Encapsulation)
- Vererbung (Inheritance)
- Polymorphismus (Polymorphism)
- Abstrakte Klassen und Methoden
- Interfaces
- Listen und Schleifen

Statt ein beliebiges Beispielprojekt zu entwickeln, verwende ich meine eigene Fantasy-Welt und ein bereits existierendes Python-Abenteuer als kreative Grundlage.

Langfristig könnten die dabei entwickelten Konzepte und Spielmechaniken auch für mein eigenes RPG-Projekt **„EAvA – Pulse of Athera“** interessant sein.

Das Lernprojekt bleibt jedoch zunächst unabhängig davon.

---

## 🎯 CURRENT GOAL

**Was ist das aktuelle Ziel, das ich erreichen will?**

Eine funktionsfähige, rundenbasierte C#-Kampfarena, die die Anforderungen der WBS-Übungsaufgabe erfüllt.

### Charaktere

- Eine abstrakte Basisklasse `Character`
- Eigenschaften wie `Name`, `Health` und `MaxHealth`
- Methoden für Angriffe, Schaden und Heilung
- Mindestens drei abgeleitete Charakterklassen mit unterschiedlichen Angriffen
- Ein Interface für Heilfähigkeiten

Die drei spielbaren Charakterklassen orientieren sich an meinem Python-Abenteuer:

- **Aegis-Ritter** – Nahkampf und Verteidigung
- **Aether-Evokator** – Magische Angriffe
- **Chronik-Schatten** – Schnelle und präzise Angriffe

### Kampfsystem

- Zwei gegnerische Gruppen mit jeweils mindestens zwei Charakteren
- Speicherung der Gruppen in `List<Character>`
- Rundenbasierter Kampfablauf
- Unterschiedliche Angriffe durch Polymorphismus
- Zufallsbasierter Schaden
- Heilfähigkeiten
- Anzeige der aktuellen Charakterwerte
- Überprüfung, ob Charaktere noch leben
- Ermittlung der Siegergruppe

### Konsolenbedienung

- Verständliche Textausgaben
- Auswahlmöglichkeiten über Konsoleneingaben
- Prüfung ungültiger Eingaben
- Übersichtliche Darstellung des Kampfverlaufs

### Projektorganisation

- C#-Konsolenprojekt mit .NET
- Klassen im Ordner `Models`
- Versionsverwaltung mit Git und GitHub
- Änderungen an `main` ausschließlich über Pull Requests
- README mit Projektbeschreibung und Anleitung
- UML-Klassendiagramm

### Definition of Done

DAS DING TUT DINGE™, wenn:

1. Das Konsolenprogramm startet.
2. Zwei Gruppen mit unterschiedlichen Charakteren gegeneinander kämpfen.
3. Angriffe und Heilung funktionieren.
4. Lebenspunkte korrekt aktualisiert werden.
5. Besiegte Charaktere nicht weiterkämpfen.
6. Das Spiel eine Siegergruppe ermittelt.
7. Ungültige Eingaben das Programm nicht zum Absturz bringen.
8. Die grundlegenden OOP-Anforderungen erfüllt sind.
9. README und UML-Diagramm vorhanden sind.

---

## 🚫 NOT NOW

**Was gehört ausdrücklich noch nicht zum aktuellen Ziel?**

Das Projekt soll zunächst eine überschaubare Lernübung bleiben.

Folgende Ideen gehören deshalb noch nicht zum aktuellen Umfang:

- Vollständige Umsetzung des Python-Abenteuers
- Umfangreiche Dialoge und verzweigte Quests
- Erkundbare Spielwelt
- Grafische Benutzeroberfläche
- Pixelart und Animationen
- Inventar- und Ausrüstungssystem
- Erfahrungspunkte und Levelsystem
- Komplexe Fähigkeiten- und Magiesysteme
- Speichersystem
- Integration in Godot
- Direkte Einbindung in „EAvA – Pulse of Athera“

Die spätere Wiederverwendung von Konzepten oder Code bleibt ausdrücklich möglich.

**NOT NOW bedeutet nicht NEVER.**

---

> 👻 Part of **KAT · DEV TOOLS** · katcoded.de
> See `DEV_TOOLS_README.md` for information about this toolkit.
