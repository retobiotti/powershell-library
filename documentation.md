# PowerShell Funktionen Bibliothek

## Inhaltsverzeichnis
1. **[Hyper-V Management](#1-hyper-v-management)**
2. **[Authentifizierung](#2-authentifizierung)**
3. **[Benutzeroberfläche](#3-benutzeroberfläche)**
4. **[Loggen](#4-loggen)**
5. **[Datenbanken](#5-datenbanken)**

## 1. Hyper-V Management
In diesem Abschnitt befinden sich funktionen, welche zusammen mit Hyper-V benutzt werden können.

### Funktion: get-vm-ipaddress
Liefert die Ip Adresse einer VM zurück, welche sich auf dem Host befindet.

```ps1
function get-vm-ipaddress (
    -vmname "VM Name"
    -type   "IPv4 oder IPv6"
)
```

**Bemerkungen** <br>
Je nach dem welcher Typ gewählt wird, wird das IPv4 oder das IPv6 Protokoll zurückgegeben. Die Funktion liefert die IPaddresse als Variable zurück, weshalb es Sinn macht, die Funktion direkt in eine Variable zu speichern.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/get-vm-ipaddress.ps1

## 2. Authentifizierung
Mit Hilfe dieser Funktionen können so genannte Credentials erstellt werden, welche in PowerShell Skripts verwendet werden können.

### Funktion: create-credential
Erstellt eine Variable welche zum Beispiel bei Remotebefehlen verwendet werden kann.

```ps1
function create-credential (
    -user       "Benutzername"
    -password   "Passwort"
    -domain     "Domäne"
    -securefile "Pfad zum Sicherheitsfile"
)
```

**Bemerkungen** <br>
Das Passwort kann in Klartext oder auch in Form eines Sicherheitsfiles mitgegeben werden.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/create-credential.ps1

### Funktion: create-credential-file
Mit Hilfe dieser Funktion kann ein Passwort einmalig in ein Sicherheitsfile gespeichert werden. Dies macht Sinn, wenn das Passwort nicht in Klartext mitgegeben werden soll.

```ps1
function create-credential-file (
    -password "Passwort"
    -filepath "Pfad zum Dokument"
)
```

**Bemerkungen** <br>
Das Passwort muss in Klartext mitgegeben werden. Die Funktion erstellt nun eine Textdatei, welche bei anderen Funktionen verwendet werden kann.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/create-credential-file.ps1

## 3. Benutzeroberfläche
In diesem Abschnitt befinden sich Funktionen, mit welchen man Windows User Interfaces bauen kann.

### Funktion: create-form-window
Erstellt ein GUI, welches mit Form Objekten befüllt werden kann.

```ps1
function create-form-window (
    -text           "Titel des Fensters"
    -bgcolor        "Hintergrundfarbe"
    -startposition  "Startpunkt des Fensters"
    -icon           "Pfad zum Icon"
    -maximize       "Maximierungsbox"
    -height         "Höhe des Fensters"
    -widht          "Breite des Fensters"
)
```

**Bemerkungen** <br>
Die gesammte Funktion muss in eine Variable gespeichert werden, damit sie später mit dem `ShowDialog()` angezeigt werden kann.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/create-form-window.ps1

### Funktion: create-form-object
Erstellt ein Objekt auf einem GUI welches zuvor erstellt wurde.

```ps1
function create-form-object (
    -form       "Variable des form-window"
    -type       "textbox, label, button, checkbox, picturebox, progressbar"
    -text       "Text"
    -value      "Wert"
    -height     "Höhe"
    -widht      "Breiete"
    -autosize   "Automatische Grösse"
    -enabled    "Aktiviert oder nicht"
    -color      "Farbe"
    -bgcolor    "Hintergrundfarbe"
    -font       "Schriftart und Grösse"
    -imagepath  "Pfad zum Bild"
    -xpos       "Abstand von oben"
    -ypos       "Abstand von links"
    -click      "Funktion welche beim Click ausgeführt wird"
    -dynamic    "Dynamische Rückgabe"
)
```

**Bemerkungen** <br>
Wird der Wert von `-dynamic` auf `$true` so liefert die Funktion ein Objekt zurück, welches im Skript weiter bearbeitet werden kann. Dies macht dann Sinn, wenn sich Text zum Beispiel von Buttons oder Labels ändern.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/create-form-object.ps1

### Funktion: create-file-dialog
Öffnet den FileDialog von Windows und liefert einen Pfad oder eine Datei zurück.

```ps1
function create-file-dialog (
    -path       "Startpfad"
    -filetype   "Filter für die Dateien"
)
```

**Bemerkungen** <br>
Standardmässig ist der Startpfad auf C:\ gesetzt. Filetypes sind Standardmässig alle Erlaubt. Weitere Filter für den WindowsFileDialog findet man hier: <br>
https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.filedialog.filter?view=netframework-4.7.2

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/create-file-dialog.ps1

## 4. Loggen
In diesem Abschnitt befinden sich Funktionen, mit welchen Rückmeldungen geloggt werden können.

### Funktion: write-log
Schreibt ein Log-File und gibt die Meldung in der Konsole aus.

```ps1
function write-log (

)
```

**Bemerkungen** <br>
Diese Funktion erstellt einen Ordner auf der Rootebene mit dem Namen Log. Meldungen welche den Namen ERROR oder WARNING enthalten werden Farblich markiert.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/write-log.ps1

## 5. Datenbanken
In diesem Abschnitt befinden sich Funktionen, welche in Verbindung mit Datenbanken verwendet werden können. Damit diese Funktionen verwendet werden können, muss ein Datenbank-Connector installiert sein. 

### Funktion: connect-database
Erstellt die Verbindung zur Datenbank. Diese Funktion muss in eine Variable umgeleitet werden.

```ps1
function connect-database (
    -dbbost     "Datenbank Host"
    -database   "Name der Datenbank"
    -user       "Benutzername"
    -pass       "Passwort"
    -port       "Port für die Verbindung"
)
```

**Bemerkungen** <br>
Diese Funktion sollte in eine Variable geschrieben werden, damit sie für das Lesen und Schreiben von Daten verwendet werden kann.

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/connect-database.ps1<>

### Funktion: read-database
Nutzt die bestehende Verbindung zur Datenbank um per SQL Statement einen Read-Befehl auszuführen.

```ps1
function read-database (
    -connection     "Verbindungsvariable"
    -sql            "Auszuführender SQL Code"
)
```

**Bemerkungen** <br>
Mit dieser Funktion können nur Daten gelesen werden!

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/read-database.ps1

### Funktion: write-database
Nutzt die bestehende Verbindung zur Datenbank um per SQL Statement einen Write-Befehl auszuführen.

```ps1
function write-database (
    -connection     "Verbindungsvariable"
    -sql            "Auszuführender SQL Code"
)
```

**Bemerkungen** <br>
Mit dieser Funktion können nur Daten geschrieben werden!

**Verwendung** <br>
Ein Beispiel zur Verwendung dieser Funktion findest du hier: <br>
https://github.com/linusniederer/powershell-library/blob/master/examples/write-database.ps1<>