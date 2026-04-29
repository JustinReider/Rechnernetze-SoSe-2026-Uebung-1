# Bericht Übungsblatt 2 – Token Ring
**Gruppe:** Marlon Schneider, Justin Reider

---

## Aufgabe 1
Repo geklont, in IntelliJ importiert und kompiliert. Lokal zwei Prozesse gestartet, Token lief problemlos.

## Aufgabe 2
Ring mit insgesamt 4 Computern im Internet aufgebaut (IPs: 2001:ac8:38:2::14; 2a07:b944::2:2; 2a02:810b:5101:5f00:5d30:b67b:b401:255e; 2a02:810b:5101:5f00:6f37:4a3d:d15f:d053). Hat nach kurzer Koordination über Discord funktioniert. Größtes Problem war die Firewall bei zwei Windows-Rechnern. Ausnahmeregel für den Port reichte als Fix. Ring lief stabil, beim Ausfall eines Knotens wurden nach 3 Retry-Versuchen automatisch aus dem Ring entfernt.

## Aufgabe 3
WireShark 4.4.3 installiert. Lokal Loopback-Interface gecaptured, im Netz das Ethernet-Interface.

Capture Filter: `tcp port 56278`  
Display Filter: `tcp.port == 56278`

Man konnte gut sehen wie der Token als kleine TCP-Nachricht weitergegeben wird. Die Verbindungen bleiben die ganze Zeit bestehen, pro Weitergabe waren ~3 Pakete sichtbar (Push + ACKs). Screenshots liegen im Repo.

WireShark 4.4.3 installiert. Lokal Loopback-Interface gecaptured, im Netz das Ethernet-Interface.
Capture Filter: udp port 56278
Display Filter: udp.port == 56278
Der Token wird als UDP-Datagramm verschickt, der Inhalt ist JSON (Sequenznummer + Liste der Ring-Mitglieder als IP/Port-Paare). Pro Weitergabe genau ein Paket, kein Verbindungsaufbau wie bei TCP.
