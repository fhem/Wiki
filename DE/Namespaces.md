# Namespaces in FHEM

## Reservierte Namespaces
Reservierte Namespaces, d.h. kein 3rd-Party-Modul soll Code in diese Namespaces ablegen, sind:
* `FHEM::Core` - Kern-Bibliotheken von FHEM, also FHEM an sich
* `FHEM::MyUtils` - Lokale, benutzerdefinierte Funktionen, die nicht veröffentlicht werden sollen


## Erweiterte Namespaces in FHEM
Erweiterte reservierte Namespaces für FHEM spezifische Module
* `FHEM::Automation` - Module welche der Automatisierung dienen. Beispiel: DOIF,notify oder AutoShuttersControl
