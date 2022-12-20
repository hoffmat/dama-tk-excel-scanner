# DAMA TK-Excel-Scanner
Java Applikation für das Parsen von Datastore TK-Excels zur Extraktion von Metadaten, die für die Verarbeitung durch den MDM-HUB bereitgestellt werden
</br>

# Anmerkung zum aktuellen Entwicklungsstand:
Der TK-Excel-Scanner wurde auf Basis der im Verzeichnis /daten/tk_excels abgelegten TK-Excel Templates und den Anforderungen, die in Confluence unter https://confluence.ruv.de:8443/confluence/display/EDD/DataStore+-+Metadaten beschrieben sind entwickelt.

Ein Test auf Basis von realen TK-Excels ist bisher nicht erfolgt. 

Da der DAMA TK-Excel-Scanner Metadaten für den Metadaten Management HUB (MDM Hub) bereitstellen soll und der MDM Hub erst im ersten Halbjahr 2023 konzipiert und umgesetzt wird, muss die Strukturen und der Inhalt der erzeugten Hub-Dateien noch angepasst werden.  

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

Es werden aktuell folgende Ausgangsdateien für den MDM-Hub erzeugt:

MDM-Hub Ausgangsdatei	Beschreibung
datastore_objects.csv	Enthält alle Objekte, die im Datenkatalog angelegt werden sollen
datastore_links.csv	Definiert die Abhängigkeiten von Objekten (Objekthierarchie)
datastore_lineage.csv	Legt die Datenflüsse zwischen Objekten fest
datastore_attributes.csv	Enthält Attribute und Attributwerte, die füe ein Objekt gelten
![image](https://user-images.githubusercontent.com/6553848/208673543-3193843f-b2a3-4a21-8f52-078706a9dc67.png)






 
# Applikationsausführung
Die Applikation wird wie folgt aufgerufen:  java -jar \<applikationsname> \<Pfad und Name des Config-Files>
 
Beispielaufruf: java -jar dama-tk-excel-scanner-0.1.0.jar C:\tmp\datastore\config.csv
