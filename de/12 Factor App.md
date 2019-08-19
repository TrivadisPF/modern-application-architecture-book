# 12 Factor App
Alleine das korrekte Anwenden der Design Prinzipien ist nicht genug, um Microservices Architecture erfolgreich umzusetzten. Es braucht auch die richtige Zusammenarbeit zwischen Entwicklern und Experten aus dem Fachbereich (domain exportes), sowie eine gute Kommunikation zwischen Teams und Teammitglieder, Continous Integration und Deliver und viele andere Dinge. 

Das Manifest “12-Factor App” wurde im Jahre 2012 von Heroku veröffentlicht und stellt eine Sammlung von Richtlinien und Best Practices für das Erstellen und Warten von skalierbaren, wartbaren und portablen Applikationen dar. Obwohl diese Prinzipien ursprünglich für die Heroku Cloud Platform erstellt wurden, gelten diese heute genauso für die erfolgreiche Umsetzung von Microservices Architekturen bzw. von cloud-native Applikationen.

### Codebasis
Sämtlicher Source Code muss in einem Version Control System eingecheckt sein und es soll eine Repository pro Applikation bzw. Microservice geben. Dies hilft sowohl beim Deployment wie auch bei der Governance. 

### Abhängigkeiten
Jeder Microservice soll seine Abhängigkeiten explizit ausweisen, deklarieren und isolieren.  Es soll nie auf systemweite Abhängigkeiten zurückgegriffen werden. Dies bedeutet in der Praxis, dass z.B. bei der Umsetzung in Java die Abhängigkeiten in Maven über das `pom.xml` oder in Gradle über das `build.gradle` File beschrieben werden. 

### Konfiguration
Die Konfiguration eines Microservices soll nicht im Code sondern über Umgebungsvariablen oder eine eigene Konfigurationsdatenbank dem Code zur Verfügung stehen. Es soll eine strikte Trennung zwischen Code und Konfiguration existieren. Der Code sollte nichts enthalten, das spezifisch für eine bestimmte Umgebung ist auf welcher der Microservice ausgerollt wird. Sämtliche Umgebungs-Spezifika sollen sich durch externe Konfigurationen ergeben. 

### Backing Services
Backing Services wie Datenbanken, Message Broker, Cache und andere Services sollten einfach austauschbar sein. Abhängigkeiten ändern sich nicht nur durch den Wechsel der Umgebung, sondern häufig auch im Laufe des Projekts. Wird der Cloud Storage Provider gewechselt, sollte diese Änderung nicht viel Aufwand am Projekt bedeuten. Darum sollten solche Services als angehängte Ressourcen behandelt werden, sodass für den Code schlussendlich kein Unterschied zwischen internen und externen Services besteht.

### Build, Run, Release
Eine 12 Factor App benötigt eine strikte Trennung zwischen den Phasen Build, Run und Release. Änderungen am Code zur Laufzeit ist strikt verboten. 
Jeder Release sollte immer eine eindeutige Release Nummer aufweisen und ein Release sollte sich auch zurückrollen lassen. Automatisierung und Verwaltung des Systems sollten so einfach wie möglich sein. So sollten Builds automatisch laufen, wenn neuer Code der Versionsverwaltung hinzugefügt wird. 

### Zustandslose Prozesse
Services sollten möglichst zustandslos sein, Applikationen sollten als einzelne, zustandslose Prozess agieren. Zustandslose Prozesse machen 12 Factor Apps stabiler. Dadurch ist die Anwendung insgesamt nicht davon abhängig, ob ein bestimmter Prozess ausfällt – ist das der Fall, läuft die App weiter und greift auf eine andere Ressource zu.  Das erhöht gleichzeitig auch die Skalierbarkeit. Dieser Faktor ist zentral in einer Microservices Architektur.

### Port Binding
Jede Anwendung muss vollständig per URL erreichbar sein. Für Web-Anwendungen gehört das sowieso zum Standard; im 12-Factor-Konzept gilt das allerdings für alle Services inklusive APIs. Andere Services sollen die Applikation als eine Ressource behandeln können. Eine 12 Factor App ist komplett eigenständig.

### Concurrency
Sollten viele kleine Prozesse zusammengefasst werden oder jeder einzeln betrieben? In diesem Modell ist die Antwort klar: Alle Prozesse laufen einzeln und können somit einzeln gestartet, beendet oder skaliert werden. Das macht es möglich, beispielsweise neue Server problemlos zu integrieren und die CPU optimal auszunutzen.

### Verfügbarkeit
Dadurch, dass Prozesse einzeln betrieben werden, können sie schnell gestartet und gestoppt werden. Die App ist somit nach einem Update quasi sofort wieder verfügbar. Außerdem sollten 12 Factor Apps möglichst robust sein, wenn es um denn Neustart nach Abstürzen geht.

### Dev-Prod Parity 
Die Entwicklungs- und Produktionsumgebung sollten so gleich wie möglich sein. Dadurch wird das berühmte „aber bei mir läuft es doch!“-Problem vermieden. Wenn die Umgebungen sich gleichen, können Testszenarios einfacher in die Realität übertragen werden, sodass weniger Fehler auftreten.

### Logs
Logs geben Auskunft über Probleme mit dem Code. Das ist wichtig. Um sicherzustellen, dass diese Logs korrekt gespeichert werden, sollte darum ein gesonderter Service verwendet werden. Das ist nicht Aufgabe des laufenden Codes, der überwacht werden soll. Interne Fehler könnten nämlich in diesem Fall auch Logfiles beschädigen. Also sollten dazu externe Services genutzt werden.

### Admin Prozesse
One-Off-Admin-Tasks sammeln wichtige Daten über das reale Verhalten einer Anwendung. Darum ist es wichtig, sie in der Produktions-Umgebung laufen zu lassen, nicht in der Entwicklungs-Umgebung oder mit einer veralteten Version des Codes. Ansonsten sind die ausgegebenen Daten nur schwer auf die real beobachteten Anwendungs-Probleme übertragbar.