# ⚔️ RPG Blerps · The Frost in Ader 4-B

<!-- KAT · DEV TOOLS | Vorlagen-Release: v1.0.0 | 2026-11-03 -->

> A turn-based console RPG built with C# and .NET as part of my Software Engineering training at WBS CODING SCHOOL.

>

> Inspired by my original fantasy adventure, "Der Frost in Ader 4-B", set in the world of Aeth'Veara.

---

## ✨ About

**RPG Blerps** is a small, turn-based battle game set in Eklésia, a city in my original fantasy world, Aeth'Veara.

Deep beneath the city's artisan district, the Aether heating system has stopped working. As frost spreads through the streets, a party of adventurers ventures into the maintenance tunnels to investigate.

There, they encounter strange creatures and malfunctioning Aether technology.

### ⚔️ Planned Gameplay

The game is being developed as a terminal-based RPG featuring:

- Turn-based party combat

- Different character classes and attack styles

- Randomized damage

- Special abilities, including healing

- Automatic enemy turns

- Character health and status displays

- A win-or-lose battle system

### 🛡️ Character Classes

The playable character types are inspired by my original Python adventure:

| Class | Combat Style |

| --- | --- |

| Aegis Knight | Melee combat and defense |

| Aether Evocator | Aether-based magical attacks |

| Chronicle Shadow | Fast and precise attacks |

### 🐀 Enemies

The arena features creatures from "Der Frost in Ader 4-B":

| Enemy | Description |

| --- | --- |

| Rust Gnawer | A rat-like creature covered in oxidized metal |

| Defective Scutter | A malfunctioning Aether-powered maintenance drone |

Character abilities and combat mechanics are still being developed.

---

## 🎓 Learning Objectives

This project is part of my Software Engineering training at **WBS CODING SCHOOL**.

Its main purpose is to practice the core principles of Object-Oriented Programming (OOP) in C#:

- **Classes & Objects** – Creating and managing game characters

- **Encapsulation** – Protecting character data and controlling health changes

- **Inheritance** – Sharing common behavior through a base character class

- **Polymorphism** – Implementing different attacks for different character types

- **Interfaces** – Adding optional abilities such as healing

The project also provides practice with:

- Lists and collections

- Loops and conditional statements

- Console input and validation

- Random number generation

- Git and GitHub workflows

- UML class diagrams

---

## 🛠️ Tech

- **C#**

- **.NET**

- **Git & GitHub**

The game uses a console interface and does not require a graphical UI framework.

---

## 🚀 Run Locally

### Prerequisites

Install the .NET SDK.

### 1 · Clone the Repository

```bash

git clone <repository-url>

```

### 2 · Open the Project

```bash

cd rpg-blerps

```

### 3 · Run the Application

```bash

dotnet run

```

> Note: The project is currently in development. The complete RPG gameplay is not yet available.

---

## 🎮 How to Play

The planned game flow is:

1. Start the console application.

2. Enter the battle arena with a party of adventurers.

3. Choose an action for each active character.

4. Select an enemy to attack or an ally to heal.

5. Survive the enemy turns.

6. Defeat the opposing party to win.

### Planned Controls

| Action | Description |

| --- | --- |

| Attack | Attack a selected enemy |

| Use Ability | Use an available special ability |

| Show Status | Display character health and status |

| Quit | Exit the game |

The final controls will be documented once the battle system is implemented.

---

## 🧩 UML Class Diagram

A UML class diagram will be added during development.

It will document:

- The abstract `Character` base class

- Derived character classes

- The `IHealer` interface

- Inheritance relationships

- Interface implementations

- Properties, methods and visibility modifiers

<!-- Add the final UML diagram here once it has been created. -->

---

## 📍 Status

**In Development · Learning Project**

The project is currently in its early development stage.

The initial .NET console project has been created, and the gameplay architecture is being planned.

Features and documentation will be updated as development progresses.

---

## 🌌 Aeth'Veara & Pulse of Athera

The setting, characters and enemies are inspired by my original fantasy universe, **Aeth'Veara**.

"Der Frost in Ader 4-B" was originally developed as a Python-based text adventure.

This C# project reimagines parts of that adventure as a small turn-based battle arena.

Some concepts and gameplay mechanics may eventually inspire or contribute to my larger game project:

**EAvA · Pulse of Athera**

However, RPG Blerps is currently an independent learning project.

---

## 👩‍💻 Developer

Built by **Kat**.

Software Engineering Student · WBS CODING SCHOOL

---

<!--

KAT-REGELN FÜR PROJECT_README

- Während der Planungs-/Vorbereitungsphase heißt diese Datei PROJECT_README.md.

- Grund: Projektinitialisierungstools wie Vite können eine README.md erzeugen bzw. eine vorhandene README kollidieren lassen.

- Erst NACH der technischen Projektinitialisierung wird aus PROJECT_README.md die finale README.md.

- Vor dem Ersetzen einer vom Setup erzeugten README kurz prüfen, ob daraus projektrelevante Setup-Informationen übernommen werden müssen.

- Danach nur EINE finale README.md behalten. Keine parallele PROJECT_README.md als zweite Wahrheit.

- README ist für Außenstehende / öffentliche Projektinformationen.

- Interner Fortschritt und Wiedereinstieg gehören in PROJECT_STATE.md.

- Brainblerps und lose interne Notizen gehören in NOTES.md.

- Die README darf mit dem Projekt mitwachsen, soll aber keine interne Projektdokumentation duplizieren.

-->

---

> 👻 Part of **KAT · DEV TOOLS** · katcoded.de

> See `DEV_TOOLS_README.md` for information about this toolkit.
