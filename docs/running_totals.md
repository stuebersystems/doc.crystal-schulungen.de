# Laufende Summenfelder

Sind Werte die sich im Laufe des Berichtsaufbaus berechnen. Diese Felder müssen keine Summen sein. Die Art der Berechnung wird beim Erstellen des Feldes festgelegt.
Die Besonderheit ist, dass laufende Summen, je in welcher Sektion diese abgelegt werden unterschiedliche Werte anzeigen, entsprechend des Aufbaus bis dahin möglichen Berechnung.

Ein Beispiel sei eine `Laufende Nummer`. Eine laufende Nummer soll mit dem Wert 1 beim 1. Datensatz einer Liste starten und dann pro Datensatz hochzählen.
Etwa wie folgt:

Nr. | Name
--- | ----
1.  | Hans
2.  | Maria
3.  | Karl
4.  | Inge

Eine solche Liste würde im `Details`- Bereich des Berichts angegeben werden.
Die laufende Summe berechnet sich in dem Moment, in dem der Datensatz durchlaufen wird.

Dies bedeutet aber auch, wenn Sie eine `Laufende Nummer` darüber angelegen (z.B. Seitenkopf, Gruppenkopf), dann wird der Startwert (= 1) angezeigt werden.
Wenn Sie eine `Laufende Nummer` darunter angelegen (z.B. Seitenfuß, Gruppenfuß), dann wird der Endwert (= 4) angezeigt werden.

<!-- ## Praktische Beispiele für Laufende Summenfelder -->

<!-- ### Erstellen einer laufenden Nummer -->
