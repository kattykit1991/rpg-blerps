# 🗺️ PROJECT BUILD GUIDE

<!-- KAT · DEV TOOLS | Vorlagen-Release: v1.0.0 | 2026-11-03 -->

> Meine Bauanleitung vom aktuellen Ziel zum funktionierenden DING™.
> Nicht in Stein gemeißelt: Wenn sich beim Bauen ein besserer Weg zeigt, darf der Bauplan mitwachsen.

---

## 🧭 BUILD ROUTE

- [STAGE 01 · Projekt startklar machen](#stage-01--projekt-startklar-machen)
- [STAGE 02 · Character-Basisklasse bauen](#stage-02--character-basisklasse-bauen)
- [STAGE 03 · Charakterklassen entwickeln](#stage-03--charakterklassen-entwickeln)
- [STAGE 04 · Heilfähigkeiten einbauen](#stage-04--heilfähigkeiten-einbauen)
- [STAGE 05 · Kampfgruppen erstellen](#stage-05--kampfgruppen-erstellen)
- [STAGE 06 · Kampfrunden entwickeln](#stage-06--kampfrunden-entwickeln)
- [STAGE 07 · Spielermenü und Eingaben](#stage-07--spielermenü-und-eingaben)
- [STAGE 08 · EAvA-Atmosphäre einbauen](#stage-08--eava-atmosphäre-einbauen)
- [STAGE 09 · Testen und Fehler beheben](#stage-09--testen-und-fehler-beheben)
- [STAGE 10 · Dokumentieren und abschließen](#stage-10--dokumentieren-und-abschließen)

---

# STAGE 01 · Projekt startklar machen

## 🎯 ZIEL

Das bestehende C#-Konsolenprojekt ist für die Entwicklung vorbereitet.

Git, GitHub und die grundlegende Projektstruktur funktionieren.

**Requirements:** FR001, FR002, FR003, FR004

## 🔨 BAUEN

### 1 · Projektstruktur überprüfen

- [ ] Prüfen, ob das bestehende Projekt mit `dotnet new console` erstellt wurde.
- [ ] Prüfen, ob `Program.cs` Top-Level-Statements verwendet.
- [ ] Prüfen, ob die `.csproj`-Datei vorhanden ist.
- [ ] Ordner `Models` für die Charakterklassen erstellen.
- [ ] Prüfen, ob `bin/` und `obj/` in `.gitignore` stehen.
- [ ] Prüfen, ob das Projekt gestartet werden kann.

#### 🧱 DAFÜR BRAUCHST DU

```bash
dotnet run
```

Startet das Konsolenprogramm.

```bash
dotnet build
```

Kompiliert das Projekt und zeigt mögliche Compilerfehler.

### 2 · GitHub-Workflow vorbereiten

- [ ] Git-Repository überprüfen.
- [ ] Öffentliches GitHub-Repository erstellen oder vorhandenes Repository prüfen.
- [ ] Prüfen, ob `main` als Hauptbranch verwendet wird.
- [ ] Feature-Branch für die erste Entwicklungsaufgabe erstellen.
- [ ] Änderungen über Pull Requests nach `main` übernehmen.

#### 🧱 DAFÜR BRAUCHST DU

```bash
git switch -c feature/example
```

Erstellt einen neuen Branch und wechselt direkt dorthin.

```bash
git status
```

Zeigt den aktuellen Zustand des Git-Repositories.

## ✅ FERTIG, WENN

- [ ] Das Konsolenprojekt startet.
- [ ] Die grundlegende Ordnerstruktur steht.
- [ ] Das öffentliche GitHub-Repository existiert.
- [ ] Der PR-Workflow ist vorbereitet.

---

# STAGE 02 · Character-Basisklasse bauen

## 🎯 ZIEL

Eine abstrakte Basisklasse bildet die gemeinsame Grundlage aller Charaktere.

Charaktere besitzen Namen und Lebenspunkte und können Schaden erhalten oder geheilt werden.

**Requirements:** FR005

## 🔨 BAUEN

### 1 · Abstrakte Klasse erstellen

- [ ] Datei `Models/Character.cs` erstellen.
- [ ] Namespace `Models` verwenden.
- [ ] Abstrakte Klasse `Character` definieren.
- [ ] Property `Name` ergänzen.
- [ ] Property `MaxHealth` ergänzen.
- [ ] Property `Health` mit privatem Setter ergänzen.
- [ ] Konstruktor für die Initialisierung erstellen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public abstract class Example
{
    public string Name { get; }
    public int Value { get; private set; }

    protected Example(string name, int value)
    {
        Name = name;
        Value = value;
    }
}
```

Eine abstrakte Klasse kann nicht direkt instanziiert werden.

`private set` verhindert, dass andere Klassen den Wert direkt verändern.

`protected` erlaubt abgeleiteten Klassen, den Konstruktor aufzurufen.

### 2 · Lebensstatus ermitteln

- [ ] Read-only-Property `IsAlive` erstellen.
- [ ] Lebensstatus anhand der aktuellen Lebenspunkte bestimmen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public bool IsAvailable => Value > 0;
```

Eine berechnete Property gibt einen Wert zurück, ohne dass dieser separat gespeichert werden muss.

### 3 · Schaden und Heilung implementieren

- [ ] Methode `TakeDamage(int amount)` erstellen.
- [ ] Verhindern, dass Lebenspunkte unter 0 fallen.
- [ ] Methode `Heal(int amount)` erstellen.
- [ ] Verhindern, dass Lebenspunkte über `MaxHealth` steigen.
- [ ] Überlegen, wie ungültige oder negative Werte behandelt werden.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
int result = Math.Max(0, value);
```

`Math.Max()` gibt den größeren der beiden Werte zurück.

```csharp
int result = Math.Min(limit, value);
```

`Math.Min()` gibt den kleineren Wert zurück.

Damit lassen sich Werte auf erlaubte Grenzen beschränken.

### 4 · Angriffsmethode vorbereiten

- [ ] Abstrakte Methode `Attack(Character target, Random random)` deklarieren.
- [ ] Noch keine konkrete Angriffslogik in der Basisklasse implementieren.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public abstract void PerformAction();
```

Eine abstrakte Methode besitzt keinen Methodenrumpf.

Abgeleitete Klassen müssen ihre eigene Implementierung bereitstellen.

## ✅ FERTIG, WENN

- [ ] Die abstrakte Basisklasse existiert.
- [ ] Properties und Konstruktor funktionieren.
- [ ] Schaden und Heilung begrenzt werden.
- [ ] `IsAlive` den Lebensstatus korrekt zurückgibt.
- [ ] Die abstrakte Angriffsmethode deklariert ist.

---

# STAGE 03 · Charakterklassen entwickeln

## 🎯 ZIEL

Mehrere Charaktertypen erben von `Character` und besitzen unterschiedliche Angriffsmechaniken.

Die Klassen orientieren sich an den Charakteren und Gegnern aus „Der Frost in Ader 4-B“.

**Requirements:** FR006, FR012, EAVA002, EAVA003

## 🔨 BAUEN

### 1 · Erste Charakterklasse erstellen

- [ ] Klasse für den Aegis-Ritter erstellen.
- [ ] Von `Character` erben.
- [ ] Konstruktor der Basisklasse aufrufen.
- [ ] Abstrakte Angriffsmethode überschreiben.
- [ ] Einen einfachen Angriff mit zufälligem Schaden implementieren.
- [ ] Den Angriff zunächst mit zwei Charakterobjekten ausprobieren.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public class ExampleChild : ExampleParent
{
    public ExampleChild(string name) : base(name)
    {
    }

    public override void PerformAction()
    {
        Console.WriteLine("Action performed.");
    }
}
```

`base(...)` ruft den Konstruktor der Basisklasse auf.

`override` überschreibt eine geerbte abstrakte oder virtuelle Methode.

### 2 · Weitere Charaktertypen ergänzen

- [ ] Aether-Evokator erstellen.
- [ ] Chronik-Schatten erstellen.
- [ ] Für beide eigene Angriffsmethoden implementieren.
- [ ] Unterschiedliche Schadensbereiche festlegen.
- [ ] Prüfen, ob alle Charaktertypen über `Character` angesprochen werden können.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public abstract class Animal
{
    public abstract void MakeSound();
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}
```

Beide Klassen besitzen dieselbe Methode, führen aber unterschiedliches Verhalten aus.

Das ist Polymorphismus.

### 3 · Gegnerklassen erstellen

- [ ] Rost-Nager als Charaktertyp erstellen.
- [ ] Defekten Scutter als Charaktertyp erstellen.
- [ ] Unterschiedliche Angriffsmechaniken definieren.
- [ ] Passende Lebenspunkte und Schadensbereiche festlegen.

### 4 · Zufälligen Schaden verwenden

- [ ] Eine gemeinsame `Random`-Instanz erstellen.
- [ ] `Random` an die Angriffsmethoden übergeben.
- [ ] Für jeden Charaktertyp einen passenden Schadensbereich verwenden.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
Random random = new Random();

int number = random.Next(1, 7);
```

`Next(1, 7)` erzeugt Werte von 1 bis einschließlich 6.

Die obere Grenze ist exklusiv.

## ✅ FERTIG, WENN

- [ ] Mindestens drei Klassen von `Character` erben.
- [ ] Jede Klasse ihre eigene Angriffsmethode besitzt.
- [ ] Angriffe unterschiedliche Schadenswerte erzeugen können.
- [ ] Rost-Nager und Scutter als Gegner verfügbar sind.
- [ ] Ein einfacher Angriff zwischen zwei Charakteren funktioniert.

---

# STAGE 04 · Heilfähigkeiten einbauen

## 🎯 ZIEL

Mindestens ein Charakter besitzt eine zusätzliche Heilfähigkeit über ein Interface.

**Requirements:** FR007

## 🔨 BAUEN

### 1 · Interface erstellen

- [ ] Datei `Models/IHealer.cs` erstellen.
- [ ] Interface `IHealer` definieren.
- [ ] Methode `Heal(Character target)` deklarieren.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public interface IExampleAbility
{
    void UseAbility();
}
```

Ein Interface beschreibt, welche Fähigkeiten eine Klasse bereitstellen muss.

### 2 · Interface implementieren

- [ ] Entscheiden, welcher Charaktertyp heilen kann.
- [ ] `IHealer` in dieser Klasse implementieren.
- [ ] Heilfähigkeit über die öffentliche `Heal(int amount)`-Methode des Ziels umsetzen.
- [ ] Sicherstellen, dass `Health` nicht direkt verändert wird.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
public class Example : IExampleAbility
{
    public void UseAbility()
    {
        Console.WriteLine("Ability used.");
    }
}
```

### 3 · Fähigkeit erkennen

- [ ] Prüfen, ob ein Charakter `IHealer` implementiert.
- [ ] Heilfähigkeit nur für passende Charaktere verfügbar machen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
if (example is IExampleAbility ability)
{
    ability.UseAbility();
}
```

Der `is`-Operator prüft den Typ und stellt gleichzeitig eine passend typisierte Variable bereit.

## ✅ FERTIG, WENN

- [ ] Das Interface existiert.
- [ ] Mindestens ein Charaktertyp es implementiert.
- [ ] Die Heilfähigkeit funktioniert.
- [ ] Andere Klassen `Health` nicht direkt verändern können.

---

# STAGE 05 · Kampfgruppen erstellen

## 🎯 ZIEL

Zwei Gruppen aus Charakteren bilden die Grundlage des Kampfsystems.

**Requirements:** FR008, FR013

## 🔨 BAUEN

### 1 · Spielergruppe erstellen

- [ ] Eine `List<Character>` für die Spielergruppe erstellen.
- [ ] Mindestens zwei Charaktere hinzufügen.
- [ ] Unterschiedliche Charaktertypen verwenden.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
List<string> names = new();

names.Add("Alpha");
names.Add("Beta");
```

Eine `List<T>` speichert mehrere Elemente desselben Typs.

Neue Elemente können mit `.Add()` ergänzt werden.

### 2 · Gegnergruppe erstellen

- [ ] Zweite `List<Character>` erstellen.
- [ ] Rost-Nager hinzufügen.
- [ ] Defekten Scutter hinzufügen.

### 3 · Statusanzeige entwickeln

- [ ] Methode für die Anzeige aller Charaktere erstellen.
- [ ] Namen ausgeben.
- [ ] Charaktertypen mit `GetType().Name` ausgeben.
- [ ] Aktuelle und maximale Lebenspunkte anzeigen.
- [ ] Besiegte Charaktere kennzeichnen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
foreach (var item in items)
{
    Console.WriteLine(item);
}
```

`foreach` durchläuft die Elemente einer Sammlung.

```csharp
Console.WriteLine(example.GetType().Name);
```

`GetType().Name` liefert den tatsächlichen Klassennamen des Objekts.

## ✅ FERTIG, WENN

- [ ] Zwei Gruppen mit jeweils mindestens zwei Charakteren existieren.
- [ ] Beide Gruppen `List<Character>` verwenden.
- [ ] Alle Charaktere mit Namen, Typ und Lebenspunkten angezeigt werden.
- [ ] Besiegte Charaktere erkennbar sind.

---

# STAGE 06 · Kampfrunden entwickeln

## 🎯 ZIEL

Ein automatischer, rundenbasierter Kampf funktioniert zunächst ohne vollständiges Spielermenü.

Jeder lebende Charakter erhält pro Runde einen Zug.

**Requirements:** FR009, FR011, FR012

## 🔨 BAUEN

### 1 · Kampfschleife erstellen

- [ ] `while`-Schleife für den Kampf erstellen.
- [ ] Prüfen, ob beide Gruppen noch lebende Charaktere besitzen.
- [ ] Kampf beenden, sobald eine Gruppe vollständig besiegt ist.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
while (condition)
{
    // Wiederhole die Aktion, solange die Bedingung erfüllt ist.
}
```

```csharp
bool hasAvailableItems = items.Any(item => item.IsAvailable);
```

`Any()` prüft, ob mindestens ein Element eine Bedingung erfüllt.

### 2 · Zugreihenfolge implementieren

- [ ] Über die Charaktere beider Gruppen iterieren.
- [ ] Besiegte Charaktere überspringen.
- [ ] Sicherstellen, dass jeder lebende Charakter höchstens einmal pro Runde handelt.
- [ ] Nach jedem Zug prüfen, ob der Kampf beendet ist.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
foreach (var item in items)
{
    if (!item.IsAvailable)
    {
        continue;
    }

    // Aktion ausführen
}
```

`continue` überspringt den restlichen Schleifendurchlauf.

### 3 · Automatische Gegneraktionen entwickeln

- [ ] Lebende Mitglieder der Spielergruppe ermitteln.
- [ ] Zufälliges Ziel auswählen.
- [ ] Gegnerangriff ausführen.
- [ ] Verhindern, dass besiegte Charaktere angegriffen werden.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
var availableItems = items
    .Where(item => item.IsAvailable)
    .ToList();
```

`Where()` filtert Elemente anhand einer Bedingung.

```csharp
int index = random.Next(availableItems.Count);
```

Erzeugt einen zufälligen gültigen Listenindex, sofern die Liste nicht leer ist.

### 4 · Kampfende ermitteln

- [ ] Prüfen, welche Gruppe noch lebende Charaktere besitzt.
- [ ] Siegergruppe ausgeben.
- [ ] Kampfschleife beenden.

## ✅ FERTIG, WENN

- [ ] Der Kampf mehrere Runden durchlaufen kann.
- [ ] Jeder lebende Charakter einmal pro Runde handelt.
- [ ] Besiegte Charaktere übersprungen werden.
- [ ] Gegner zufällige lebende Ziele angreifen.
- [ ] Der Kampf bei vollständiger Niederlage einer Gruppe endet.

---

# STAGE 07 · Spielermenü und Eingaben

## 🎯 ZIEL

Der Spieler kann seine Charaktere während des Kampfes selbst steuern.

**Requirements:** FR007, FR010

## 🔨 BAUEN

### 1 · Zugmenü erstellen

- [ ] Angreifen anbieten.
- [ ] Heilfähigkeit anbieten, falls vorhanden.
- [ ] Gruppenstatus anzeigen lassen.
- [ ] Spiel beenden ermöglichen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
Console.WriteLine("1. Option A");
Console.WriteLine("2. Option B");

string? input = Console.ReadLine();
```

`Console.ReadLine()` liest eine Eingabe aus der Konsole.

### 2 · Eingaben überprüfen

- [ ] Leere Eingaben erkennen.
- [ ] Nichtnumerische Eingaben erkennen.
- [ ] Ungültige Menüoptionen abfangen.
- [ ] Bei ungültigen Eingaben erneut fragen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
if (string.IsNullOrWhiteSpace(input))
{
    Console.WriteLine("Bitte etwas eingeben.");
}
```

```csharp
if (int.TryParse(input, out int number))
{
    Console.WriteLine(number);
}
```

`TryParse()` versucht, einen Text in eine Zahl umzuwandeln, ohne bei ungültiger Eingabe eine Exception auszulösen.

### 3 · Zielauswahl entwickeln

- [ ] Verfügbare Ziele nummeriert anzeigen.
- [ ] Zielnummer abfragen.
- [ ] Prüfen, ob die Nummer gültig ist.
- [ ] Besiegte Ziele ausschließen.

### 4 · Heilfähigkeit ins Menü integrieren

- [ ] `IHealer` mit dem `is`-Operator prüfen.
- [ ] Heiloption nur für passende Charaktere anzeigen.
- [ ] Heilziel auswählen lassen.
- [ ] Heilfähigkeit ausführen.

### 5 · Menü mit Kampfschleife verbinden

- [ ] Spieleraktionen in den bestehenden Kampfablauf integrieren.
- [ ] Statusanzeige ermöglichen, ohne dadurch einen Kampfzug zu verbrauchen.
- [ ] Ungültige Eingaben dürfen keinen Kampfzug verbrauchen.
- [ ] Quit-Option beendet das Spiel kontrolliert.

## ✅ FERTIG, WENN

- [ ] Der Spieler Angriffe selbst auswählen kann.
- [ ] Heilfähigkeiten nur bei passenden Charakteren angeboten werden.
- [ ] Ziele über Nummern ausgewählt werden.
- [ ] Ungültige Eingaben abgefangen werden.
- [ ] Das Spiel kontrolliert beendet werden kann.

---

# STAGE 08 · EAvA-Atmosphäre einbauen

## 🎯 ZIEL

Die funktionierende Kampfarena erhält die Atmosphäre von „Der Frost in Ader 4-B“.

Die Ergänzungen bleiben bewusst klein und verändern nicht die grundlegende Kampfmechanik.

**Requirements:** EAVA001, EAVA002, EAVA003, EAVA004

## 🔨 BAUEN

### 1 · Einführung gestalten

- [ ] Kurzen Einstieg in Eklésia schreiben.
- [ ] Die Unteren Tiegel als Schauplatz vorstellen.
- [ ] Die ausgefallene Aether-Heizleitung erwähnen.
- [ ] Den Übergang zur Kampfarena herstellen.

### 2 · Charaktere und Gegner präsentieren

- [ ] Passende Anzeigenamen verwenden.
- [ ] Charakterklassen kurz vorstellen.
- [ ] Rost-Nager und Scutter atmosphärisch beschreiben.

### 3 · Kampfmeldungen gestalten

- [ ] Unterschiedliche Angriffsmeldungen formulieren.
- [ ] Heilaktionen verständlich ausgeben.
- [ ] Niederlagen passend beschreiben.
- [ ] Sieg und Niederlage mit kurzen Abschlusstexten versehen.

#### 🧱 DAFÜR BRAUCHST DU

```csharp
Console.WriteLine($"{name} führt eine Aktion aus!");
```

String-Interpolation ermöglicht es, Variablen direkt in Text einzufügen.

### 4 · Spielablauf überprüfen

- [ ] Sicherstellen, dass die zusätzlichen Texte die Spiellogik nicht verändern.
- [ ] Prüfen, ob Konsolenausgaben übersichtlich bleiben.

## ✅ FERTIG, WENN

- [ ] Die Arena eindeutig in Eklésia angesiedelt ist.
- [ ] Die Charaktere zur EAvA-Welt passen.
- [ ] Kampfmeldungen Atmosphäre vermitteln.
- [ ] Die WBS-Kernanforderungen weiterhin erfüllt sind.

---

# STAGE 09 · Testen und Fehler beheben

## 🎯 ZIEL

Die Kampfarena funktioniert zuverlässig und erfüllt die definierten Requirements.

Testergebnisse werden in `PROJECT_TESTING.md` dokumentiert.

## 🔨 BAUEN

### 1 · Charaktermechaniken überprüfen

- [ ] Schaden reduziert Lebenspunkte korrekt.
- [ ] Lebenspunkte fallen nicht unter 0.
- [ ] Heilung erhöht Lebenspunkte korrekt.
- [ ] Heilung überschreitet `MaxHealth` nicht.
- [ ] `IsAlive` erkennt besiegte Charaktere.
- [ ] Unterschiedliche Charaktertypen verwenden ihre eigenen Angriffsmethoden.

### 2 · Kampfsystem überprüfen

- [ ] Beide Gruppen besitzen mindestens zwei Charaktere.
- [ ] Jeder lebende Charakter handelt einmal pro Runde.
- [ ] Besiegte Charaktere handeln nicht mehr.
- [ ] Gegner wählen nur lebende Ziele.
- [ ] Der Kampf endet beim Sieg einer Gruppe.
- [ ] Der Kampf endet bei Niederlage der Spielergruppe.

### 3 · Eingaben überprüfen

- [ ] Leere Eingabe testen.
- [ ] Buchstaben statt Zahlen testen.
- [ ] Ungültige Menüoptionen testen.
- [ ] Ungültige Zielnummern testen.
- [ ] Heiloption bei Charakteren ohne `IHealer` überprüfen.
- [ ] Quit-Option überprüfen.

### 4 · Technische Prüfung durchführen

- [ ] Projekt mit `dotnet build` kompilieren.
- [ ] Projekt mit `dotnet run` starten.
- [ ] Einen vollständigen Kampf durchspielen.
- [ ] Gefundene Fehler beheben.
- [ ] Nach Korrekturen erneut testen.

#### 🧱 DAFÜR BRAUCHST DU

```bash
dotnet build
dotnet run
```

### 5 · Requirements überprüfen

- [ ] FR001–FR015 anhand der tatsächlichen Umsetzung prüfen.
- [ ] EAVA001–EAVA004 überprüfen.
- [ ] Implementation-Status aktualisieren.
- [ ] Review-Status nur bei tatsächlich erfolgter Prüfung aktualisieren.
- [ ] Offene Probleme dokumentieren.

## ✅ FERTIG, WENN

- [ ] Das Projekt ohne Compilerfehler gebaut werden kann.
- [ ] Mindestens ein vollständiger Kampf erfolgreich durchgespielt wurde.
- [ ] Kritische Eingabefehler abgefangen werden.
- [ ] Testergebnisse dokumentiert sind.
- [ ] Offene Probleme bekannt sind.

---

# STAGE 10 · Dokumentieren und abschließen

## 🎯 ZIEL

Das Projekt ist dokumentiert, nachvollziehbar und für die Präsentation vorbereitet.

**Requirements:** FR003, FR014, FR015

## 🔨 BAUEN

### 1 · UML-Klassendiagramm erstellen

- [ ] Alle relevanten Klassen darstellen.
- [ ] `Character` als abstrakte Klasse kennzeichnen.
- [ ] Vererbungspfeile einzeichnen.
- [ ] `IHealer` als Interface darstellen.
- [ ] Interface-Realisierung kennzeichnen.
- [ ] Properties und Methoden ergänzen.
- [ ] Sichtbarkeiten (`+`, `-`, `#`) darstellen.

#### 🧱 DAFÜR BRAUCHST DU

```text
+ public
- private
# protected
```

UML verwendet Symbole zur Darstellung der Sichtbarkeit.

### 2 · README vervollständigen

- [ ] Projekt kurz vorstellen.
- [ ] Voraussetzungen nennen.
- [ ] Startanleitung ergänzen.
- [ ] Spielablauf erklären.
- [ ] Steuerung dokumentieren.
- [ ] Charaktertypen vorstellen.
- [ ] UML-Klassendiagramm einbinden.
- [ ] Herkunft der EAvA-Inspiration erwähnen.

### 3 · GitHub-Projekt abschließen

- [ ] Letzte Änderungen committen.
- [ ] Feature-Branch pushen.
- [ ] Pull Request erstellen.
- [ ] Änderungen überprüfen.
- [ ] Pull Request nach `main` mergen.
- [ ] Öffentlichen Repository-Stand kontrollieren.

### 4 · Abschlussprüfung durchführen

- [ ] README-Anleitung selbst ausprobieren.
- [ ] UML-Diagramm mit dem tatsächlichen Code vergleichen.
- [ ] Requirements abschließend prüfen.
- [ ] Projektstatus aktualisieren.
- [ ] Präsentation entsprechend den Instructor-Vorgaben vorbereiten.

## ✅ FERTIG, WENN

- [ ] Das UML-Klassendiagramm vollständig ist.
- [ ] Das README Start und Bedienung erklärt.
- [ ] Das Projekt im öffentlichen GitHub-Repository verfügbar ist.
- [ ] Änderungen über Pull Requests nach `main` gelangt sind.
- [ ] Die Requirements abschließend überprüft wurden.
- [ ] Das Projekt für eine mögliche Präsentation vorbereitet ist.

---

<!--
KAT-REGELN FÜR DEN BAUPLAN

- Die BUILD ROUTE oben bleibt als schnelle Gesamtübersicht erhalten.
- Der Guide wird von oben nach unten benutzt. Seine Reihenfolge soll deshalb der echten Bearbeitungsreihenfolge entsprechen.
- Erst steht, WAS ich konkret bauen soll. Direkt danach kommt, WAS ich dafür technisch brauchen könnte.
- CODE-BAUSTEINE sind generische Lernmuster, keine fertigen Lösungen für das aktuelle Projekt.
- Nicht jeder Bauschritt braucht zwingend einen Code-Baustein.
- Planungslücken sind erlaubt. Wenn das echte Bauen einen fehlenden Schritt zeigt, darf der Bauplan angepasst werden.
- Der Bauplan ist eine Route, kein Vertrag.
-->

---

> 👻 Part of **KAT · DEV TOOLS** · katcoded.de  
> See `DEV_TOOLS_README.md` for information about this toolkit.
