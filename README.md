# llearn Hardwarebeschreibung

*Bilder im Ordner bilder/* !!!

## outline
Die zweite Ausführung der LLearn Hardware wurde etwas umfangreicher. Vorhanden sind:
* Raspberry Pi 3
* Selbstentwickelte Headerplatine für RPi3 (Daten im Ordner board/)
    * MPU6050 als Lagesensor
    * SHT21 als Raumtemperatursensor
    * MCP3208 Analog-Digital-Converter mit SPI Schnittstelle
* Stromzähler mit s0-Schnittstelle

Der Raspberry Pi 3 ist ein Entwicklerboard mit einer ARMv8 CPU und 1 GB RAM. Folgende
Schnittstellen zur Kommunikations sind verfügbar:
* LAN
* WLAN
* Bluetooth
* 40-PIN GPIO Header mit:
    * SPI
    * I2C
    * UART
* SD Karte

Für den Raspberry Pi 3 wurde eine Headerplatine (Daten im Ordner board/) entwickelt,
die unterschiedliche benötigte Schnittstellen enthält:
* MCP3208
    * Ein Analog-Digital-Converter, der mit Photowiderständen die Helligkeit der
    LEDs der Waschmaschine misst um zu ermittelt, ob die LED an ist oder nicht.
* SHT21
    * ein Temperatur und Luftfeuchtigkeitssensor
* MPU6050
    * ein 3-Achsen Beschleunigungs und Neigungssensor, der einen "Schüttelwert"
    beim Schleudern und den aktuellen Status des Drehrads aufnimmt.

Gebootet wird der LLearn Pi von einer SD Karte in das Betriebssystem Raspbian
in der Version Jessie. Dies ist das offizielle Debian Derivat für den Raspberry Pi.
Mit dem Internet verbunden ist das Gerät über WLAN. Nach dem Boot wird der llearnd
daemon gestartet. Dieser übernimmt die Abfrage der Hardwareperipher und S0 Schnittstelle.
Außerdem übernimmt er die Analyse der GPIO Date, die Kommunikation mit dem Internet (MQTT
Broker), die Ausführung von zusätzliches Skripten (Machine Learning) und das Logging.
Er ist praktisch als zentrale Logikstelle des Projektes zu sehen.

## files
### llearn-eagle-zip
Zipfile mit EAGLE Schaltplanfiles zur Headerplatine
### board/
#### llearn-board.pdf
Boardlayout für die Headerplatine des Raspberry Pi 3
#### llearn-schaltplan.pdf
Schaltplan für die Headerplatine

### bilder/
Diverse Fotos zur projekthardware
