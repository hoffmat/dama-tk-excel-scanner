# DAMA TK-Excel-Scanner
Java Applikation für das Parsen von Datastore TK-Excels zur Extraktion von Metadaten, die für die Verarbeitung durch den MDM-HUB bereitgestellt werden.
</br>

# Anmerkung zum aktuellen Entwicklungsstand:
Der TK-Excel-Scanner wurde auf Basis der im Verzeichnis /daten/tk_excels abgelegten TK-Excel Templates und den Anforderungen, die in Confluence unter https://confluence.ruv.de:8443/confluence/display/EDD/DataStore+-+Metadaten beschrieben sind entwickelt.

Es ist bisher kein Test auf Basis von realen TK-Excels erfolgt. 

Da der DAMA TK-Excel-Scanner Metadaten für den Metadaten Management Hub (MDM Hub) bereitstellen soll und der MDM Hub erst im ersten Halbjahr 2023 konzipiert und umgesetzt wird, müssen die Strukturen und der Inhalte der erzeugten Hub-Dateien noch angepasst werden.
</br>
Außerdem muss ein End-to-End Integrationstest durchgeführt werden (TK-Excel-Scanner -> MDM Hub -> Informatica Enterprise Data Catalog)

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

datastore_objects.csv	   --> enthält alle Objekte, die im Datenkatalog angelegt werden sollen
</br>
datastore_links.csv	     --> definiert die Abhängigkeiten von Objekten (Objekthierarchie)
</br>
datastore_lineage.csv	   --> legt die Datenflüsse zwischen Objekten fest
</br>
datastore_attributes.csv	--> enthält Attribute und Attributwerte, die füe ein Objekt gelten


# Konfigurationsdatei
Die Applikation liest beim Programmstart Parameter aus einer Konfigurationsdatei
</br>
Die Konfigurationsdatei muss im csv-Format abgelegt sein. 
Der Name und der Pfad der Datei sind beim Programmstart als Applikationsparameter angegeben werden.

Parameter werden in der Konfigurationsdatei im Format <parametername>,<parameterwert> angegeben (ohne Quotes)  
// am Zeilenanfang wird als Kommentar erkannt  
Zeilen, die mit * beginnen werden ignoriert

Aktuell werden folgende Parameter verwendet:

quellverzeichnis	   --> gibt an, wo die TK-Excels abgelegt sind
</br>
zielverzeichnis	   --> gibt an, wo die MDM-Hub Dateien und die Logging-Datei abgelegt werden
</br>  
attributewhitelist	   --> legt die gültige Attributmenge fest
</br>
attribunamedefaults --> legt die gültige Attributmenge fest, für die Default-Werte gesetzt werden sollen 
</br>
attributwertdefaults --> legt die gültige Default-Werte für die Default-Attribute fest (Null = es wird Defaultwert gesetzt)


# Applikationsausführung
Die Applikation wird wie folgt aufgerufen:  java -jar \<applikationsname> \<Pfad und Name des Config-Files>
 
Beispielaufruf: java -jar dama-tk-excel-scanner-0.1.0.jar C:\tmp\datastore\config.csv
