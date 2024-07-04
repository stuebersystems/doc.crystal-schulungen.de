# Crystal Reports Formeln

In vielen Fällen sind die für einen Bericht benötigten Daten bereits in den Feldern einer Datenbanktabelle enthalten. So würden Sie beispielsweise für eine Schülerliste die für diesen Zweck nötigen Felder einfach in den Bericht aufnehmen.

Gelegentlich müssen aber auch Daten in den Bericht eingefügt werden, die in keinem der Datenfelder enthalten sind, erst innerhalb des Berichtes interpretiert werden müssen oder Daten, die aus vorhandenen Feldern berechnet werden.

Zum Einfügen solcher Daten bietet Crystal Reports den Formel-Editor. Sie haben die Möglichkeit eine Formel zu erstellen und diese als Formelfeld in den Bericht mit einzufügen.

## Komponenten und Syntax von Formeln

In Formeln können Sie verschiedene Komponenten verwenden und müssen eine bestimmte Syntax (die Grammatik-Regeln zur Programmierung einer Formel) einhalten.
Im folgenden Listen wir die möglichen Formelkomponenten auf und Beschreiben wie sie in den Formeln eingesetzt werden (also die Syntax).
Einige der Komponenten wie z.B. `Strukturen` werden in weiteren Kapiteln detaillierter erklärt.

Komponente               | Beispiel                           | Erklärung
------------------------ | ---------------------------------- | ---------
Felder                   | {Schueler.Geburtsdatum}            | Datenbankfelder werden in geschweiften Klammern nach dem Muster {Tabellenname.Feldname} dargestellt
Zahlen                   | 1,2,3...5192                       | Zahlen werden einfach so eingetippt
Text                     | "Ihr freier Text"                  | Texte, die nicht aus der Datenbank kommen, sondern einfach so in einer Formel zur Ausgabe angegeben werden, müssen in Anführungszeichen stehen
Operatoren               | + Addieren<br>- Subtrahieren<br>/ Dividieren<br>-x Vorzeichenwechsel | Operatoren können Sie wie in einem mathematischen Term verwenden
Funktionen               | Round(x), Trim(x)                  | Mit Funktionen werden Rechenvorgänge wie beispielsweise Mittelwertberechnung, Summenbildung und Zählung durchgeführt. Alle verfügbaren Funktionen sind zusammen mit ihren Argumenten nach Verwendung geordnet geführt und können auch in der Crystal-Online-Hilfe (F1) nachgelesen werden. Viele Funktionen erwarten Parameter, diese werden dann in runden Klammern nach dem Schlüsselwort (Funktionsname) gesetzt
Strukturen               | „If“, „Select“ und „For“-Schleifen | Kontrollstrukturen bzw. Bedingungen
Werte von Gruppenfeldern | Average(Feld, BedFeld), Sum(Feld, BedFeld, „Bedingung“) | In Gruppenfeldwerten wird eine Gruppe zusammengefasst. Sie können Gruppenfeldwerte beispielsweise dazu verwenden, den prozentualen Anteil jeder Gruppe am Gesamtbetrag zu ermitteln
Andere Formeln           | {@Adresse}, {@Volljaehrig}         | Formeln können in anderen Formeln verwendet werden. So werden Formeln auch in der Entwurfsansicht angezeigt, mit dem At-Zeichen (auch Klammeraffe genannt). Wenn Sie bestehende Berichte bearbeiten, werden Sie auf solche Felder stoßen. Dahinter verbergen sich dann die Formeln, die Sie auch jederzeit ansehen, bearbeiten und für Ihre Berichte kopieren können.

## Formel-Syntax in Crystal Reports

Beim Erstellen von Formeln haben Sie die Wahl, entweder die Syntax von Crystal oder die Syntax von Basic zu verwenden. Fast jede Formel die in einer Syntax geschrieben wurde, kann auch in der anderen Syntax geschrieben werden. In Berichten können gleichzeitig Formeln in Basic-Syntax und Formeln in Crystal Syntax enthalten sein.
STÜBER SYSTEMS verwendet in Berichten die Basic Syntax, die auf Visual Basic aufbaut. Wenn Sie schon einmal mit Visual-Basic zu tun hatten, werden Sie umso schneller in die Formel-Programmierung mit Crystal Reports einsteigen.

## Die Basic-Syntax

Eine Formel muss mindestens aus einem Ausdruck bestehen, nämlich der Ergebnisvariablen. Die Ergebnisvariable ist in der Basic-Syntax festgelegt und lautet `formula`.

### Beispiel

Formel               | Ergebnis der Formel | Erläuterung
-------------------- | ------------------- | -----------
formula = 10 + 3     | 13                  | Hier werden die Komponente `Zahl` und der Operator `+` verwendet, um zwei Zahlen miteinander zu addieren und dieses als Ergebnis der Formel auszugeben
formula = „männlich“ | männlich            | Hier wird die Komponente `Text` verwendet, um lediglich das Wort "männlich" als Ergebnis der Formel auszugeben

Dies ist der kleinste anzunehmende Fall einer Formel. Die Formel ist somit abgeschlossen und gültig. Im `Feld-Explorer` von Crystal erscheint die Formel unter `Formel-Felder`, nachdem Sie die Formel mit einem frei zu vergebenen Namen abgespeichert haben.

### Kommentare

Sie können Formeln mit Kommentaren versehen. Dies ist insofern interessant, wenn Sie zum einen mit mehreren Kollegen an Berichten arbeiten, aber auch wenn Sie besonders komplexe Formeln als Gedankenstütze mit Beschreibungen versehen möchten. Kommentare sind rein deskriptiv, werden nicht ausgegben und können nur beim Bearbeiten der Formeln eingesehen werden.

Kommentare funktionieren pro Zeile und müssen mit einem Schlüsselwort vorangestellt werden.

Schlüsselwort | Beispiel
------------- | --------
rem           | rem Dies ist ein Kommentar mit rem
'             | ' Dies ist ein Kommentar mit Hochkomma (Shift-Raute)
'             | ' Dies ist eine Zeile mit Kommentar<br>' Dies ist eine zweite Zeile mit Kommentar

### Datentypen

Jedes in einer Formel verwendete Feld bzw. jede Variable gehört zu einem bestimmten Typ. Folgende einfache Feldtypen stehen in Formeln zur Verfügung.

Typ      | Bedeutung             | Beispiel
-------- | --------------------- | --------
Number   | Zahl                  | 1,2,3,4,5,6,7,8,9,0
Currency | Währung               | 13,90€
String   | Zeichenfolge          | "Hallo“, "weiblich“
Boolean  | Logischer Wert        | TRUE (wahr) oder FALSE (falsch)
Date     | Datum                 | 01.01.2013
Time     | Zeit                  | 14:20:01
DateTime | Datum und Zeitstempel | 01.01.2013 14:20:01

### Variablen

Variablen werden benötigt, um Werte zwischenzuspeichern, die in der Formel weiterverarbeitet, berechnet bzw. später in der Formel wieder benötigt werden.
Variablen werden mit dem Schlüsselwort `Dim` deklariert und einem Datentyp zugewiesen.

Deklaration                 | Erläuterung                              | Mögliche Werte
--------------------------- | ---------------------------------------- | --------------
Dim Zahl as Number          | Eine Variable vom Typ Zahl               | Ganze und Kommazahlen
Dim Betrag as Currency      | Eine Variable vom Typ Währung            | Währungsbeträge 3,50 €
Dim Text as String          | Eine Variable vom Typ Text               | "Hallo“, "weiblich“
Dim IstEsWahr as Boolean    | Eine Variable vom Typ logischer Wert     | TRUE (wahr) oder FALSE (falsch)
Dim Stichtag as Date        | Eine Variable vom Typ Datum              | 01.01.2013
Dim Zeit as Time            | Eine Variable vom Typ Zeit               | 14:20:01
Dim Zeitstempel as DateTime | Eine Variable vom Typ Datums-Zeitstempel | 01.01.2013 14:20:01

### Programmstrukturen

Das Auswerten der Formeln erfolgt von Crystal Reports sequenziell, das heißt die Formel wird von oben nach unten Zeile für Zeile durchgearbeitet. Programmstrukturen können diese feststehende Abfolge ändern. Durch Bedingungen kann abhängig gemacht werden, welche Zeilen bzw. Anweisungen ausgeführt werden und welche übersprungen werden sollen.

#### If - Anweisung (Wenn-dann-sonst-Fall)

Mit der If-Anweisung können Sie Bedingungen definieren, so genannte Wenn-Fälle.
In der Schülertabelle steht z.B. beim Geschlecht des Schülers nur ein "M" und ein "W" für männlich und weiblich. Um im Bericht "männlich" oder "weiblich" stehen zu haben, müssen wir eine Formel schreiben, die die Werte abfragt und als Resultat der Formel für M „männlich“ und für W „weiblich“ zurückgibt.

Basic Syntax | Beschreibung
------------ | ------------
If {Schueler.Geschlecht} = „M“ then<br>&nbsp;&nbsp;formula = „männlich“<br>else<br>&nbsp;&nbsp;formula = “weiblich“<br> end if | Wenn das Schüler Geschlecht = M ist, dann<br>&nbsp;&nbsp;soll der Wert der Formel = „männlich“ sein,<br>sonst<br>&nbsp;&nbsp;soll der Wert der Formel = „weiblich“ sein<br>  Ende der Bedingung

#### Select-Anweisung

Die Select-Anweisung ähnelt der If-Anweisung. Soll der Wert auf mehrere Fälle hin überprüft werden, werden die Formeln mit der Select-Anweisung übersichtlicher.

Basic Syntax | Beschreibung
------------ | ------------
Select Case Fehlstunden<br>&nbsp;&nbsp;Case 0<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = „Keine Stunden“<br>&nbsp;&nbsp;Case 1<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = „1 Stunde, davon“<br>&nbsp;&nbsp;Case Else<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = CStr(Fehlstunden, 0) & „Stunden, davon“<br>End Select | Im Falle dass Fehlstunden<br>&nbsp;&nbsp;Fall 0<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = „Keine Stunden“<br>&nbsp;&nbsp;Fall 1<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = „1 Stunde, davon“<br>&nbsp;&nbsp;sonstiger Fall<br>&nbsp;&nbsp;&nbsp;&nbsp;Teil1 = Umwandeln der Zahl Fehlstunden in Text & „Stunden, davon“<br>Ende der Select Anweisung

### Gängige Funktionen

#### PageNumber

Gibt die jeweilige Seitennummer zurück. Sie wird z.B. in Kombination mit der Funktion `mod` (modulo) verwendet, um zwischen geraden und ungeraden Seiten zu unterscheiden.

#### Mod

Ist die mathematisch modulo Funktion, um den Restwert einer Division zu berechnen.

* **Format**: x mod y
* **Beispiel**: 2 mod 4 = 0

Angewendet wird die Funktion unter anderem mit der Funktion `PageNumber`.

* **Beispiel**: PageNumber mod 2

Ist das Ergebnis 0 ist die Seitenzahl gerade.

#### RecordNumber

Gibt die jeweilige Datensatznummer zurück. Wird auch gerne mit der Funktion `mod` benutzt.

* **Beispiel**: PageNumber mod 2

Ist das Ergebnis 0 ist der aktuelle Datensatz gerade.
Wird z.B. für abwechselnd farbige Zeilen in einer Tabelle verwendet.

#### Count(Wert)

Gibt die Anzahl von etwas zurück.

#### ToText(Wert)

Wandelt einen Zahlentyp in einen Texttyp um, damit dieser als Text ausgegeben werden kann.

#### ToText(Wert,Wert)

Wie `ToText(Wert)` mit zusätzlichem Parameter für die Anzahl der Dezimalstellen.

#### UpperCase(Wert)

Gibt den Text in Großbuchstaben an.

#### Truncate(Wert)

Ausschneiden eines Teiles aus einem Feld.

#### Truncate(Wert,Wert)

Wie `Truncate()`. Ausschneiden einer Zahl mit Angabe der Dezimalstellen.

#### OnLastRecord

Gibt den letzten Datensatz wider. Wird in Verwendung mit manuellen Seitenumbrüchen verwendet, wenn auf der Letzten Seite, also nach dem letzten Datensatz kein weiter Umbruch stattfinden soll. Diese Funktion wurde hauptsächlich bis Version 2011 verwendet.

Ab Crystal Reports 2011 gibt es eine entsprechende Option, um einen Seitenumbruch nach dem Gruppenfuß einzufügen, leere Seiten werden automatisch vermieden.

### Praktische Beispiele

Die einfachste sinnvolle Verwendung einer Formel fügt mehrere Datenbankfelder und evtl. festen Text zusammen.

#### Felder zusammensetzen

Das folgende Beispiel fügt den Vor- und Nachnamen des 1. Klassenleiters zu einem Formelfeld zusammen. Vorausgesetzt, dass ein Klassenleiter1 in Magellan eingetragen wurde.

```vb
1 formula = ““
2
3 If ( {KlassenZeitraeume.Klassenleiter1} > 0 ) then
4 formula = ({KlassenZeitraeume.Nachname} + “, “ + _
5          ({KlassenZeitraeume.Vorname}
6 end if
```

Der Unterstrich am Ende der Zeile 3 erlaubt die Anweisung in zwei Zeilen (4 und 5) einzugeben, anderenfalls würde die Formel als fehlerhaft gelten. Sie können die Zeilen 4 und 5 auch alles in eine Zeile schreiben und benötigen den Unterstrich dann nicht.

#### Anrede umwandeln

In vielen Fällen werden in der Datenstruktur Platzhalter für bestimmte Werte in Magellan gespeichert, u. a. bei der Anrede. Welche Bedeutung sich hinter den Platzhalterwerten befinden können Sie in der [Magellan-Datenstruktur}(https://doc.magellan7-toolbox.stueber.de/datenstruktur/) lesen.

Solche Werte müssen für Berichte in lesbare Ausgabewerte umgewandelt werden.

```vb
Select Case {Sorgeberechtigte.Anrede}
Case “0“
  formula = “Frau“
Case “1“
  formula = “Herr“
Case “2“
  formula = “Frau Dr.“
…
End Select
```
