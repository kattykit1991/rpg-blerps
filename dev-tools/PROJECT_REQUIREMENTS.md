# 📋 PROJECT REQUIREMENTS

<!-- KAT · DEV TOOLS | Vorlagen-Release: v1.0.0 | 2026-11-03 -->

> Was muss DAS DING™ erfüllen – und was wurde tatsächlich überprüft?

> Anforderungen, Implementierung und Review bleiben getrennt.

---

## 🎯 PURPOSE

Hier stehen die Anforderungen dieses Projekts: **Was muss am Ende funktionieren oder erfüllt sein?**

Die Tabelle zeigt getrennt, ob eine Anforderung bereits **umgesetzt** und ob sie anschließend tatsächlich **geprüft** wurde.

<!--

Falls eine Aufgabenstellung bereits Requirements oder IDs (z. B. FR001) vorgibt:

- Originalformulierungen und Kennzeichnungen möglichst unverändert übernehmen.

- Keine neuen Anforderungen dazuerfinden.

- Wenn noch keine Requirements existieren, können sie später ergänzt werden.

- Die Platzhalterzeile unten durch echte Anforderungen ersetzen oder entfernen.

-->

## 📌 REQUIREMENTS

### 🎓 WBS · Original Requirements

Die folgenden Anforderungen stammen aus der offiziellen WBS-Aufgabenstellung „Console RPG Arena“.

| ID | Functional Requirement | Description | Implementation | Review |

| --- | --- | --- | --- | --- |

| FR001 | Solo Project | Work independently; no team members. | Open | Not Reviewed |

| FR002 | Single Public Repository | Keep all code in one GitHub repo; instructors are not collaborators. | Open | Not Reviewed |

| FR003 | PR-Only Workflow | Push all changes to main exclusively through Pull Requests. | Open | Not Reviewed |

| FR004 | Project Setup | Create the app with dotnet new console and use top-level statements in Program.cs. Put your classes in separate files in a Models folder with a Models namespace. | Open | Not Reviewed |

| FR005 | Base Class Character | An abstract class with Name, Health and MaxHealth. Health has a private setter. Add a read-only property IsAlive, a method TakeDamage(int amount) that never lets Health go below 0, and a public method Heal(int amount) that never lets Health go above MaxHealth. | Open | Not Reviewed |

| FR006 | Character Types | At least three classes that inherit from Character (for example Warrior, Mage, Rogue). Each one overrides an abstract Attack(Character target, Random random) method with its own behaviour. | Open | Not Reviewed |

| FR007 | Special Ability Interface | Define an interface such as IHealer with a method Heal(Character target). At least one character type implements it by calling target.Heal(amount), because the private setter stops other classes from changing Health directly. During a turn, check whether the active character is an IHealer with the is operator before offering the option. | Open | Not Reviewed |

| FR008 | Parties | Store the player’s party and the enemies in two List<Character> collections. Each side has at least two characters. | Open | Not Reviewed |

| FR009 | Battle Loop | Run the battle in a while loop. Each round, every living character acts once. The loop ends when every character on one side has IsAlive == false. | Open | Not Reviewed |

| FR010 | Turn Menu | On each player turn, show a menu: attack, use ability (only if available), show status, quit. Choose targets by number. Reject empty or invalid input with string.IsNullOrWhiteSpace and int.TryParse. | Open | Not Reviewed |

| FR011 | Enemy Turns | Enemies act automatically: they attack a random living member of the player’s party. | Open | Not Reviewed |

| FR012 | Random Damage | Damage varies within a range per character type. Use a single Random instance and pass it to the methods that need it. | Open | Not Reviewed |

| FR013 | Status Display | A method that prints every character’s name, type and health, and marks defeated characters. Get the type name with GetType().Name. | Open | Not Reviewed |

| FR014 | UML Class Diagram | Draw a UML class diagram of your game (classes, interface, inheritance and realisation arrows, visibility modifiers), as in the OOP Design exercise. | Open | Not Reviewed |

| FR015 | README | Document how to run the game, how to play, and include the UML diagram. | Open | Not Reviewed |

### 🐉 EAvA · Project Requirements

Die folgenden Anforderungen sind eigene Ergänzungen für die thematische Gestaltung der Arena.

Sie erweitern die WBS-Aufgabe, ersetzen oder verändern aber keine ihrer Vorgaben.

| ID | Requirement | Implementation | Review |

| --- | --- | --- | --- |

| EAVA001 | Die Kampfarena spielt in Eklésia, im Handwerkerviertel „Die Unteren Tiegel“, und orientiert sich am Abenteuer „Der Frost in Ader 4-B“. | Open | Not Reviewed |

| EAVA002 | Die drei spielbaren Charaktertypen orientieren sich an Aegis-Ritter, Aether-Evokator und Chronik-Schatten. | Open | Not Reviewed |

| EAVA003 | Die gegnerische Gruppe enthält einen Rost-Nager und einen defekten Scutter. | Open | Not Reviewed |

| EAVA004 | Die Konsolenausgaben vermitteln die Atmosphäre des ursprünglichen Abenteuers durch kurze Beschreibungen und passende Kampfmeldungen. | Open | Not Reviewed |

<!--

STATUSWERTE IN V1.0.0 – einfache Ausgangswerte; weitere Zwischenstände bei echtem Bedarf klar benennen:

Implementation:

- Open: Noch nicht begonnen.

- In Progress: In Bearbeitung.

- Done: Implementierung abgeschlossen; sagt noch nichts über den Review aus.

Review:

- Not Reviewed: Noch keine Prüfung durchgeführt.

- In Review: Prüfung läuft.

- Passed: Tatsächlich geprüft; Anforderung erfüllt.

- Changes Required: Prüfung hat Korrekturbedarf ergeben.

Andere Zwischenstände bei Bedarf klar benennen; keine künstlichen Häkchen setzen.

-->

---

## 🔎 REVIEW NOTES

Kurze Notizen **nur dann ergänzen, wenn tatsächlich eine Prüfung stattgefunden hat**. Keine leeren Review-Protokolle für jede Anforderung nötig.

<!--

BEISPIELSTRUKTUR (kein echtes Review-Ergebnis):

### [ID]

- Geprüft: [Code / Verhalten / Tests / Anforderungen]

- Ergebnis: [Beobachtungen und Nachweise]

- Korrekturen / Follow-up: [Was ist noch offen?]

Falls die Prüfung Probleme findet, den Review nicht als Passed markieren.

Falls konkrete Testfälle in PROJECT_TESTING.md den Review belegen, bei Bedarf ihre IDs angeben – keine Testergebnisse doppelt dokumentieren.

Nach einer Korrektur erneut prüfen, bevor Passed eingetragen wird.

-->

---

## 🧭 KAT-REGELN FÜR REQUIREMENTS

- **Implementation ≠ Review.** Fertig programmiert ist nicht automatisch erfolgreich geprüft.

- **Nur belegte Ergebnisse eintragen.** Keine bestandenen Tests oder Reviews behaupten, die nicht durchgeführt wurden.

- **Requirements originalgetreu halten.** Die Datei beschreibt _was_, nicht die ausführliche Schrittfolge zur Umsetzung.

- **Keine doppelte Projektpflege.** Entwicklungsschritte gehören in `PROJECT_BUILD_GUIDE.md`; der aktuelle Wiedereinstiegsstand in `PROJECT_STATE.md`.

- **Kompakt bleiben.** Akzeptanzkriterien, Testdetails oder weitere Abschnitte nur ergänzen, wenn das Projekt sie wirklich braucht.

- **Keine zusätzlichen Agentenregeln.** Zuständigkeiten und Schreibrechte regelt `AGENTS.md`.

---

> 👻 Part of **KAT · DEV TOOLS** · katcoded.de

> See `DEV_TOOLS_README.md` for information about this toolkit.
