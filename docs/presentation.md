# Präsentation

Notizen und Folien aus der Crystal Reports Einführungsschulung.

## Wissenswertes zu Crystal Reports

* Integrierte Runtime–Version in Magellan zum Drucken bestehender Berichte
* Sie benötigen eine Volllizenz zum Ändern von Berichten
* Die Volllizenz kann bei SAP erworben werden
* Letzte aktuelle Version 2020.

## Was ist eine relationale Datenbank?

### Wichtige Merkmale einer relationalen Datenbank

!![Was ist eine relationale Datenbank - Teil I](/assets/images/powerpoint/was-ist-eine-relationale-datenbank-1.png)

* Daten werden in Tabellenform gespeichert.
* Eine Zeile über alle Spalten wird Datensatz genannt
* In den einzelnen Felder stehen die Daten
* Sie werden nach gewissen Kriterien in den Spalten angelegt, z.B. „Vorname“

!![Was ist eine relationale Datenbank - Teil II](/assets/images/powerpoint/was-ist-eine-relationale-datenbank-2.png)

* Tabellen können miteinander verknüpft werden.
* Sie stehen somit in Relation (Beziehung) zueinander.
    * Standardmodell für Datenbanken.
    * Daten werden weitestgehend redundanzfrei (nicht doppelt) gespeichert.
    * Sehr einfacher, logischer Aufbau.
    * Leicht abfragbar durch SQL (Standard Datenbank Abfrage Sprache).

## Datenbanken abfragen

!![Datenbank abfragen](/assets/images/powerpoint/datenbanken-abfragen.png)

* Abfragen in der Datenbank werden über die Datenbank-Abfragesprache SQL getätigt.
* SQL steht für „Structured Query Language“.
* SQL ist der Standard zum Abfragen und Manipulieren von Datenbanken.
* Magellan  und Crystal Reports nutzen intern SQL um Daten der Datenbank anzuzeigen, neu anzulegen oder zu ändern.
* SQL Kenntnisse sind zur Nutzung von Crystal Reports nicht direkt nötig, erklärt aber warum manche Schritte in
Crystal Report gemacht werden (z.B. Verknüpfung: `Left Outer Join`)

## Aufbau eines Berichtes

!![Berichtsaufbau](/assets/images/powerpoint/berichtsaufbau.png)

* `Berichtskopf` und `Berichtsfuß`: Erscheinen jeweils nur einmal im Ausdruck.
* `Seitenkopf` und `Seitenfuß`: Erscheinen auf jeder Seite im Ausdruck.
* `Details`: Erscheinen immer nach dem Seitenkopf (hier werden die Daten ausgegeben: entweder jeder Datensatz auf eine Seite oder alle Datensätze hintereinander).
* `Gruppenkopf` und `Gruppenfuß`: Sind optional und vorerst im Bericht nicht sichtbar. Beide können jeweils einmal pro Gruppe oder auch auf jeder Seite angezeigt werden.
