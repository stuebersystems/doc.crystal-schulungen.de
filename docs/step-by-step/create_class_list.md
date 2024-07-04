# Eine Klassenliste von Grund auf neu erstellen

Grundlegend müssen Sie sich überlegen, ob ein bestehender Bericht abgeändert werden kann? Machen Sie sich nicht mehr Arbeit als nötig. STÜBER SYSTEMS liefert für jede Berichtskategorie mehrere Berichte. Die Grundlegenden Tabellenverknüpfungen bleiben größtenteils gleich. Sie ersparen Sie viel Zeit und Mühe, wenn Sie einen vorhandenen Bericht einfach an Ihre Wünsche anpassen. Sollte keiner der Berichte annährend an Ihre Wünsche herankommen, dann sollten Sie Crystal Reports starten und einen neuen Bericht erstellen.

## Neuen Bericht anlegen

Standardmäßig wird Crystal Reports mit dem Willkommens-Dialogfenster gestartet. Sollte das Dialogfenster nicht erscheinen, so klicken Sie im Hauptmenü auf `Datei > Neu > Leerer Bericht`.

![Leerer Bericht](/assets/images/stept-by-step/create-class-list/file.new.empty-report.png)

## Mit Datenbank verbinden

Es öffnet sich der Datenbank-Assistent. Hier muss die Quelle der Daten, also zum einen die Magellan-Verbindung und zum anderen die Tabellen ausgewählt werden. Crystal Reports kann nicht direkt auf die Magellan-Datenbank zugreifen. Bei der Installation von Magellan wird deshalb ein ODBC-Treiber (Standard Datenbanktreiber) mitinstalliert, der es Crystal Reports ermöglicht auf die Datenbank zuzugreifen.

Um die Verbindung auszuwählen klicken Sie auf `+ Zeichen` von `Neue Verbindung herstellen` und dann auf das `+ Zeichen` von `ODBC (RDO)`.

![Datenbank-Assistent - Datenquelle wählen](/assets/images/stept-by-step/create-class-list/assistant.database.select-datasource.png)

Es öffnet sich ein Dialogfenster zur Auswahl der ODBC-Datenquelle. Die Verbindung für Magellan zu Crystal-Reports nennt sich `Magellan-CR`. Wählen Sie diese aus und klicken Sie auf `Weiter`.

![Datenbank Assistent - ODBC-Verbindung wählen](/assets/images/stept-by-step/create-class-list/assistant.database.select-odbc.png)

Sie kommen auf eine weitere Seite in dem die Anmeldung bei der Datenbank erfolgen muss. Es wird der Benutzer (Standard: `SYSDBA`) und Passwort (Standard: `masterkey`) eingegeben und danach mit `Fertig stellen` bestätigt. Damit erhält man Zugriff auf die Magellan-Datenbank über Crystal Reports. Sollten Sie sich vertippt haben, kann es sein, dass sich ein anderes Dialogfenster öffnet, in dem Sie die Anmeldedaten erneut eintragen sollen.

![Datenbank Assistent - Anmelden](/assets/images/stept-by-step/create-class-list/assistant.database.odbc-credentials.png)

Das Dialogfenster schließt sich und Sie können nun auf die Magellan-Datenbank zugreifen. Dies erkennen Sie daran, dass sich unterhalb ODBC in der Hierarchie jetzt der Eintrag `Magellan-CR` befindet und diese weitere Einträge `Tabellen` und `Ansichten` zeigt, auf die nun zugegriffen werden kann, um die entsprechenden Datentabellen für den Bericht auszuwählen.

![Datenbank Assistent - Verbunden](/assets/images/stept-by-step/create-class-list/assistant.database.connected.png)

## Benötigte Tabellen und Ansichten auswählen

!!! info "Hinweis"

    **Unterschied zwischen Tabellen und Ansichten** In `Tabellen` werden die Daten organisiert und gespeichert. Jür jede logische Einheit gibt es eine Tabelle. `Ansichten` sind Abfragen auf die Datenbank, die Felder aus einer oder mehrere Tabellen zusammenfassen. Ansichten werden fest in der Datenbank gespeichert und sind schneller als einzelne Abfragen, darüber hinaus können diese zusätzlich mit Rechten versehen werden.

![Datenbank Assistent - Auswahl einer Tabelle/Ansicht](/assets/images/stept-by-step/create-class-list/assistant.database.select.png)

!!! info "Hinweis"

    In der Auswahl-Ansicht stehen immer die Auswahlkriterien, die in Magellan zum Drucken eines Berichtes benötigt werden. Welche Auswahltabelle Sie benötigen erkennen Sie daran, welche Berichtskategorie Ihr Bericht angehört. Ein Bericht für Lehrer, nutzt die Ansicht `AuswahlLehrer`, ein Bericht für Schüler die `AuswahlSchüler`.

1. Öffnen Sie links die `Ansichten`
2. Wählen Sie die passende Auswahl-Ansicht, für Klassenbericht ist dies die Ansicht `AuswahlKlassen`. Per Doppelklick, oder über die Schalftfläche mit dem `Pfeil nach Rechts` können Sie die Ansicht als `Ausgewählte Tabelle` für den Bericht übernehmen.
3. Wiederholen Sie die Schritte für alle weiteren Tebellen/Ansichten, die in ihrem Bericht verwendet werden. Für unsere Klassenliste fügen Sie bitte folgendes hinzu:

### Ansichten

Name    | Erläuterung
------- | -----------
Lehrer2 | Enthält eine verkürzte Ansicht der Lehrer-Stammdaten. Auf diese dürfen Benutzer mit niedriegeren Benutzerrechten zugreifen. Während auf die `Lehrer` - Ansicht nur Benutzer mit höheren Zugriffsrechten zugreifen dürfen.

![Ansicht "Lehrer2"](/assets/images/stept-by-step/objects/view.lehrer2.png)

Lehrer kommen in unterschiedlichen Rollen in Magellan vor. Als Schulleitung, Stellv. Schulleitung, Klassenleiter 1 und Klassenleiter 2 oder z.B. als Tutor, oder Fachlehrer. In der Datenbank wird jeweils die für den Lehrer eindeutige ID des Datensatzes gespeichert. Um in Crystal Reports an die Stammdaten des Lehrers zu kommen, muss die entsprechende Ansicht/Tabelle hinzufgefügt und auf den passenden Lehrer gefiltert werden. Da diese Filterung auf einen Lehrer mit entsprechender Rolle verweist, müssen wir ggfs. diese Ansicht/Tabelle mehrfach in den Bericht einbinden, z.B. einmal als Klassenleiter 1 und einmal als Klassenleiter 2.

Dabei ergibt sich ein Namensproblem und ggf. ein Verständnisproblem, dem wir mit einer klärenden Umbenennung begegnen. Wir benennen die Ansicht/Tabelle nach dem Muster <originalname_Rolle\> um.

![Ansicht "Lehrer2" - Alias umbenennen](/assets/images/stept-by-step/create-class-list/assistant.database.rename-alias.png)

### Tabellen

Name               | Erläuterung
------------------ | -----------
Klassen            | Stammdaten der Klasse (Kürzel, Langname1, Langname2, ...)
KlassenZeitraueme  | Zeitraumbezogene Daten zur Klasse (z.B. Verweis auf den Klassenleiter1 und Klassenleiter2, ...)
Schueler           | Stammdaten der Schüler (Namen, Adresse, etc.)
SchuelerZeitraeume | Zeitraumbezogene Daten zum Schüler (Fehlzeiten, Verweis auf aktuelle Ausbildung, Kopfnoten, ...)

## Verknüpfen / Daten vorfiltern

Das Auswählen der Tabellen für den Bericht bezieht diese letztendlich in die Abfrage ein, die Crystal Reports auf die Magellan-Datenbank macht. Die Abfrage auf die Datenbank muss sich aber auf die gewählten Datensätze (in Magellan markierte Klassen) beziehen. Die Klassen wurden in einem bestimmten Zeitraum (1. oder 2. Halbjahr eines Schuljahres) und für einen bestimmten Mandanten (üblicherweise ihre Schule) markiert. Dies haben Sie in Magellan beim Druck nicht explizit ausgewählt, aber Ihre Filter sind entsprechend gesetzt.

![Magellan - Auswahl für den Druck](/assets/images/stept-by-step/create-class-list/magellan.classes.select.png)

Wenn Sie eine Tabelle/Ansicht hinzufügen werden grundsätzlich alle Daten zur Verfügung gestellt. Aus dem Grund müssen die Tabellen/Ansichten auf Ihre Auswahl gefiltert werden. Diese Filterung wird durch Verknüpfen der entsprechenden Felder miteinander, durchgeführt.

### Regeln beim Verknüpfen

1. Der Ursprung ist die Auswahl-Ansicht `AuswahlKlassen`. Hier stehen die von ihnen gewählten Klassen, mit dem passenden Zeitraum und Mandanten (jeweils die IDs)

2. Verknüpfungen werden von einem Feld einer Tabelle auf ein Feld einer anderen Tabelle vollzogen. Quellfeld markieren, klicken, ziehen und auf Zielfeld loslassen.

3. Die zu verknüpfenden Felder meinen logisch das Gleiche. Zum Beispiel (AuswahlKlassen.Klasse > SchuelerZeitraeume.Klasse, da in beiden Tabellen die Klassen.ID gemeint ist)

4. Es kann immer nur von **einer** Tabelle auf eine andere Tabelle verknüpft werden. Also nicht von zwei Tabellen auf eine

5. Sie müssen für alle Verknüpfugen die Verknüpfungsoption "Left Outer Join" (Linke äussere Verknüpfung) auswählen. Dazu Doppelklick auf eine Verknüpfungslinie.

![Datenbank Assistent - Verknüpfungsoption](/assets/images/stept-by-step/create-class-list/assistant.database.verknuepfen-option.png)

### Gesamtes Verknüpfungsbild

Für unser Beispiel ergibt sich folgendes Verknüpfungsbild.

![Datenbank Assistent - Verknüpfungen](/assets/images/stept-by-step/create-class-list/assistant.database.verknuepfen.png)