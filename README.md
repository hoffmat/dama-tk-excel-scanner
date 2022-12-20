# DAMA TK-Excel-Scanner
Java Applikation für das Parsen von Datastore TK-Excels zur Extraktion von Metadaten, die für die Verarbeitung durch den MDM-HUB bereitgestellt werden
</br>

# Anmerkung zum aktuellen Entwicklungsstand:
Der TK-Excel-Scanner wurde auf Basis der im Verzeichnis /daten/tk_excels abgelegten TK-Excel Templates und den Anforderungen, die in Confluence unter https://confluence.ruv.de:8443/confluence/display/EDD/DataStore+-+Metadaten beschrieben sind entwickelt.

# Eingangsdaten
Die Applikation verarbeitet TK-Excel Dateien. Die Dateien müssen in einem Verzeichnis abgelegt werden, dass in der Konfigurationsdatei config.csv als Parameter angegeben wird.

Beispiel config.csv:
</br>
// Quellverzeichnis in dem die Datastore Excel-Files gesucht werden
</br>
quellverzeichnis,C:\tmp\datastore\tk_excels\

Beispiel TK-Excel Dateien sind im Verzeichnis /daten/tk_excels abgelegt

# Ausgangsdaten
Die Applikation verarbeitet TK-Excel Dateien, extrahiert hieraus Metadaten und stellt diese Metadaten in Form von csv-Dateien zur Verfügung. Die Ausgangsdateien werden in das Zielverzeichnis geschrieben, welches in der Konfigurationsdatei config.csv als Parameter angegeben ist.


Beispiel config.csv:
</br>
// Zielverzeichnis in dem die Datastore Excel-Files gesucht werden
</br>
zielverzeichnis,C:\tmp\datastore\hub\

</br>

 
# Applikationsausführung
Die Applikation wird wie folgt aufgerufen:  java -jar \<applikationsname> \<Pfad und Name des Config-Files>
 
Beispielaufruf: java -jar dama-tk-excel-scanner-0.1.0.jar C:\tmp\datastore\config.csv
