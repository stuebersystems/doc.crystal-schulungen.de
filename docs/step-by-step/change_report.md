# Einen bestehenden Bericht abändern

## Daten zum Testen vorbereiten

Bevor Sie den Bericht zum Ändern aufrufen, sollten Sie Testdaten in den Speicher laden, die während der Berichtsänderung immer wieder überprüft werden können.

Dafür gehen Sie in MAGELLAN an die Stelle, in der der abzuändernde Bericht üblicherweise ausgedruckt wird. Hier ein Beispiel anhand einer Klassenliste.

1. Öffnen Sie die Ansicht `Klassen` 
2. Markieren Sie in der `Auswahlliste` eine oder mehrere Klassen. 
3. Gehen Sie den üblichen Weg, um Berichte für diese Klassen auszudrucken. Anstatt die Berichte zu drucken, lassen Sie sich diese in der `Vorschau` anzeigen. 
   Durch den Aufruf der Vorschau (dies passiert auch wenn man auf drucken geht) wird die entsprechende Auswahltabelle (hier `AuswahlKlassen`) gefüllt, in der die Auswahldaten stehen.
4. Schließen Sie das Dialogfenster zum Druck wieder.

## Bericht öffnen

Wechseln Sie zu `Extras > Berichte organisieren`. Sie sollten sich im Klaren sein, welchen Bericht Sie ändern möchten. Ein Doppelklick auf den Bericht öffnet diesen in Crystal Reports.

## Bericht testen

Der Bericht öffnet sich in der Entwurfsansicht von Crystal Reports. Die Seitenansicht ist noch geschlossen. Klicken Sie im Hauptmenü `Bericht` auf den Unterpunkt `Berichtdaten aktualisieren`. Einfacher geht es mit der Taste F5.

Die Seitenansicht öffnet sich. Beim ersten Öffnen der Seitenansicht erscheint eine Meldung, Ihre Benutzerdaten für die Datenbank wären nicht verfügbar. Klicken Sie auf OK. Es öffnet sich ein Dialogfenster zur Anmeldung an die Datenbank. Geben Sie bitte den Benutzernamen(Standard: `SYSDBA`) und Ihr Kennwort(Standard: `masterkey`) ein und bestätigen mit OK.

Wenn Sie keinen Fehler bei der Anmeldung gemacht haben, sollten Sie sich jetzt in der Seitenansicht wieder finden. Sie müssten die Daten des Berichtes sehen, wie zuvor in der MAGELLAN Druckvorschau.

Als nächstes wird der Bericht unter neuem Namen abgespeichert, damit der Originalbericht nicht überschrieben wird. Dazu gehen Sie auf den Hauptmenüpunkt `Datei` und dann auf `Speichern unter…`. Wählen Sie das Verzeichnis und geben Sie der Datei einen neuen Namen. STÜBER SYSTEMS nutzt für die Namensgebung der Berichte eine eigene Namenskonvention, die Sie gerne übernehmen können. Diese wird in der Dokumentation der [Landesanpassungen](http://doc.la.stueber.de/#berichtsdateinamen) beschrieben.

## Bericht ändern

Jetzt kann der Bericht in der Entwurfsansicht nach Wunsch geändert werden.
