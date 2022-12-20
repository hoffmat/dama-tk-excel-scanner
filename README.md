# DAMA TK-Excel-Scanner
Java Applikation für das Parsen von Datastore TK-Excels zur Extraktion von Metadaten, die für die Verarbeitung durch den MDM-HUB bereitgestellt werden
</br>

# Eingangsdaten
Die Applikation verarbeitet TK-Excel Dateien. Die Dateien müssen in einem Verzeichnis abgelegt werden, dass in der Konfigurationsdatei config.csv als Parameter angegeben wird.


Beispiel config.csv:
</br>
// Quellverzeichnis in dem die Datastore Excel-Files gesucht werden
</br>
quellverzeichnis,C:\tmp\datastore\tk_excels\

</br>

# Ausgangsdaten
Die Applikation verarbeitet TK-Excel Dateien, extrahiert hieraus Metadaten und stellt diese Metadaten in Form von csv-Dateien zur Verfügung. Die Ausgangsdateien werden in das Zielverzeichnis geschrieben, welches in der Konfigurationsdatei config.csv als Parameter angegeben ist.


Beispiel config.csv:
</br>
// Zielverzeichnis in dem die Datastore Excel-Files gesucht werden
</br>
zielverzeichnis,C:\tmp\datastore\hub\

</br>

 
