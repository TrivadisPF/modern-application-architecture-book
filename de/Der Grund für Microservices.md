# Microservices

## Definition

*Microservices sind unabhängig deploybare Module*

## Was ist ein Microservice

Microservices zeichnen sich dadurch aus, dass jeder Service für sich genommen lediglich einen kleinen, in sich mehr oder minder geschlossenen Teil der Anwendung abbildet. Die durch ein Team umzusetzende Fachlichkeit ist in der Regel leicht zu verstehen und zu beherrschen. Selbst technologisch ist ein einzelner Service deutlich einfacher zu handhaben als ein Monolith. Im Idealfall ist ein Microservice unabhängig erweiterbar, austauschbar und skalierbar. Richtig umgesetzt funktioniert die Anwendung auch noch dann, wenn ein Service nicht verfügbar ist.

So wie es scheint, bringen Microservices eine Menge Vorteile mit sich. Allerdings kommt ein Microservice per Definition selten allein. Die Komplexität der Anwendung verlagert sich, im Vergleich zum Monolithen, auf das korrekte Zusammenspiel der Services. Wie also müssen die Services geschnitten sein, um die eben aufgeführten Bedingungen – unabhängig erweiterbar, austauschbar und skalierbar – in einer auf Microservices basierenden, stark verteilten Architektur zu erfüllen? 

## Zentrale Eigenschaften eines Microservices

- **Nur eine Aufgabe:*** Jeder Microservice ist nur für eine Aufgabe (capability) verantwortlich. Dies solle im Normalfall eine fachspezifische Aufgabe sein, ein Microservice kann aber auch eine technische Aufgabe (z.B. Integration eines Umsystems) umfassen

- **Microservice besitzt seine Daten, sofern er welche verwaltet:** Dies heisst aber nicht, dass der Microservices zwingend einen eigene Datenbank-Instanz besitzen muss. Wichtig ist nur, dass es eine klare Abgrenzung gibt und diese nicht umgangen werden kann (d.h. die Grenze kann eine eigne Tabelle, ein Namensraum wie z.B. ein Schema oder aber eine komplette Instanz sein). Dies führt zu besserer Entkoppelung, da andere Service auf die Daten, die sie nicht besitzen nur über die Schnittstellen zugreifen können. 

- **Verantwortet Choreography und Zusammenarbeit:** Die Microservices sind für die Choreography und die Zusammenarbeit zwischen Microservices verantwortlich und nicht die Nachrichten-Platform dazwischen. 

- **Lässt sich unabhängig ausliefern:** Jeder Microservice lässt sich unabhängig ausliefern. Ohne dies wäre eine Microservice Applikation zur Laufzeit weiterhin ein Monolith.

- **Lässt sich einzeln ersetzten:** Der Umfang eines Microservices soll für jedes Teammitglied überschaubar sein und mit vertretbarem Zeitaufwand (ca. 1 Monat) komplett neu erstellt und ersetzt werden können. 

- **Implementiert einen Bounded Context:** Ein Microservice soll einen Bounded Context im Sinne von Domain Driven Design implementieren.

- **Von einem Team verantwortet:** Ein Microservice wird immer von einem Team entwickelt und auch betrieben.

- **Gut isoliert:** Microservices werden gegenüber den anderen Services so gut wie möglich isoliert

- **Nutzung des Technologie-Stack, der am Besten passt:** Ein Microservice soll den Technologie-Stack nutzen, die es für ihn am einfachsten macht, die Aufgabe umzusetzen. 

Zusätzlich zu diesen Eigenschaften haben Microservices eine Ähnlichkeit mit UNIX Kommandos. Beide sind ausführbare Einheiten mit einer einzigen Aufgabe und können über Standard-Schnittstellen zu etwas grösserem zusammengebaut werden. Im Falle von UNIX Kommandos sind die Standard-Schnittstellen stdin und stdout bzw. stderr und die Kommunikation geht über die Unix Pipes. Im Falle von Microservices kann eine Schnittstelle über verschiedene Protokolle wie HTTP, AMQP, gRPC oder Kafka realisiert werden, die von der Macro-Architektur entsprechend unterstützt werden. 

## Was sind Microservices nicht?
In den frühen Tagen von Microservices gab es einige Missverständnisse und Unklarheiten rund um das Thema Microservices. Mit dem beliebter werden des Begriffes Microservices wurden diese Missverständnisse und damit die fehlerhafte Nutzung nur noch grösser. 

Die folgenden Umsetzungen haben nichts mit der Idee von Microservices zu tun

* **Ein einfaches API zu einem komplexeren Service, der Teil einer monolithischen Applikation ist.** Der Entwurf und der Umfang von einem API sollte unabhängig von der Implementierung sein. In diesem Fall würde man den Service einen "Macroservice" nennen. 
* **Ein Service der durch eine geringe Codemenge realisiert ist.** Die Anzahl Codezeilen ist nicht relevant, wenn sich der Service nicht unabhängig deployed und betrieben werden kann. 
* **Ein Service, der ohne Test-, Deployment- und Betriebs-Automatisierung entwickelt und ausgeliefert wird.** Eine Microservices Architektur ist der Ansatz das Ausliefern und den Betrieb von Applikationen in skalierbarer Art und Weise unterstützen. Ohne Automatisierung ist das Risiko eines menschlichen Fehlers viel zu hoch.
* **Ein Service, der auf einer "mutable" Infrastruktur betrieben wird, die separat und unabhängig von der Softwareauslieferung ge-patched und aktualisiert wird.** Eine stabile und berechenbare Infrastruktur ist zentral für den Betrieb von Microservices. Änderungen an dem unterliegenden Betriebsystem oder Laufzeitumgebung, die nicht die gleichen rigorosen und automatisierten Test- und Deployment-Prozesse nutzen, die für Codeanpassungen verwendet werden, sind hart zu wiederholen, nicht deterministisch und erhöhen das Fehlerrisiko. 
* **Ein Service mit Abhängigkeiten zu anderen Services, die verhindern dass er unabhängig geändert und aktualisiert werden kann.** Kopplung zwischen den Services, die zur Folge haben, dass diese bei einer Änderung synchron angepasst werden müssen, erzeugen einen "distributed monolith". Microservices sollen nur Abhängigkeiten über klar definierte Schnittstellen auf andere Service haben und sollten erlauben, dass die Service-Implementierung unabhängig geändert werden kann. 
* **Ein grosser, grob-granularer Service oder ein monolithisches Set von Services, die als Docker Container paketiert wurden.**. Containerisierung macht alleine keine Microservices. Es ist nur ein möglicher Software Paktetierungs- und Auslieferungs-Mechanismus. Docker und andere Container Modelle sind hilfreiche Werkzeuge für die Definition einer Auslieferungseinheit (Code und dessen Abhängigkeiten) für einen Microservice, es ist aber nicht die einzige Möglichkeit. 
* **Ein Service wird als API von einer anderen Partei zur Verfügung gestellt.** Unabhängig davon wie der Service implementiert wurde, wenn man die Implementierung nicht kontrolliert, dann handelt es sich hierbei "nur" um einen Service aus Sicht meiner Applikation. 
* **Eine Komponente, ein Modul, ein Service, eine Eigenschaft, über die ich aber keine Kontrolle bezüglich Auslieferung und Verwaltung habe, die konsistent zu den anderen Microservices ist, wird von einem Hersteller als Microservice bezeichnet.** Etwas als Microservice zu bezeichnen ist eine beliebte Masche, um die Aufmerksamkeit der Kunden zu gewinnen. Die Vorteile von MSA haben viel mit der Organisation und Prozessmodellen zu tun, die sie unterstützen. Man kann diese Vorteile nicht einfach mit einem Produkt einkaufen, es kann aber nach einem Produkt gesucht werden, dass sich nahtlos in eine MSA einbetten lässt. 
* **Ein publiziertes API, das intern oder extern zu einer Organisation genutzt werden kann.** MSA ist ein Implementierungsdetail, das von der Publizierten Schnittstellenspezifikation getrennt werden soll. API Konsumenten sollten nicht wissen bzw. sollten sich nicht darum kümmern, ob die Implementation dahinter auf einer Microservices Architektur oder einer traditionelleren Applikationsarchitektur basiert, oder aber eine Integrationsplatform genutzt wird.

## Vorteile von Microservices

Die folgende Vorteile kann der Einsatz von Microservices bringen:

* **Schnelleres Deployment:** Microservices machen die Deployment-Lebenszyklen viel flexibler, indem die Entwicklung und Auslieferung von einzelnen, unabhängigen Services entkoppelt wird, so dass einzelne, agile Teams den Prozess von Continous Delivery praktizieren können.   

* **Erhöhte Flexibilität beim Deployment:** Microservices unterstützten die Teams in der agilen und dynamischen Weiterentwicklung der Applikationen mit reduziertem Risiko. 

* **Präzisere Skalierbarkeit:** Microservices führen zu besser skalierbaren Applikationen, da jederzeit zusätzliche Service Instanzen in Betrieb genommen werden können, um zusätzliche Kapazität für spezifische Funktionalitäten hinzuzufügen. Zudem kann ein Microservice bei Bedarf eine spezifische Technologie, um seine Aufgabe effizient durchführen zu können. 

## Herausforderungen

Microservices Architekturen haben nicht nur Vorteile, sondern halten auch Herausforderungen bereit:

* **Der Betrieb eines Systems bestehend aus vielen Microservices ist aufwendiger als der Betrieb einer monolithischen Applikation.** Der Grund ist, dass in einem Microservice-System viel mehr eigenständige Einheiten existieren, die unabhängig deployed und überwacht werden müssen. Das ist nur machbar, wenn das ganze möglichst automatisiert ist.
* **Microservices müssen unabhängig und getrennt deploybar sein.** Docker Container stellen dafür eine wichtige Basis zur Verfügung, dies alleine reicht aber nicht aus. Auch das Testen muss getrennt werden . Wenn alle Microservices zusammen getestet werden müssten, dann gehen alle Vorteile der Unabhängigkeit beim Testen gleich wieder verloren.


