# Microservices Architecture

## Zwei Architecture Viewpoints

* **Die Mikro Architektur (auch Inner Architecture genannt):** Die Software Architektur von einem individuellen Microservices und was er nach Aussen exponiert. Wird durch die DevOps Teams definiert, die die Services entwickeln, ausliefern und betreiben. 
* **Die Makro Architektur (auch Outer Architecture genannt):** Die Architektur der Microservices Infrastruktur, die eine verteilte Betriebs- und Management-Platform zur Verfügung stellt, auf die die Services ausgerollt und ausgeführt werden. Wird vom Platform Ops Team definiert, ausgerollt und betrieben und unterstützt damit die Arbeit der DevOps Teams. 

    
### Makro Architektur

Aufgrund der Inversionf of Architecture, die

I mentioned that due to the Inversion of Architecture, many of the concerns that used to be solved at the inner architecture level of the monolith have now become the outer architecture concerns. Figure 4-14 attempts to show schematically the concerns we need to address at the outer architecture level of a microservice. Microservices interact with each other and this chattiness between process spaces increases the overall complexity. Concerns like fault tolerance, graceful retry, and alternate code execution are few among them and this necessitates strong management, monitoring, and control of microservices at its outer architecture level. The goal is to achieve agility of delivery, flexibility of deployment, and the precision of scalability in a microservices architecture. In order to do this, a new set of concerns must be addressed and this increases the complexity of microservices manyfold compared to that of a monolith.


### Mikro Architektur
   
The examples of different inner architectures shown in Figure 9 are not exhaustive, but show some of the most common patterns:

* **Basic logic:** Dieser Microservices ist zustandslos und braucht keinen Persistenzdienst. Diese Art von Service wird genutzt um rechenintensive Jobs durchzuführen, wie z.B. eine Berechung einer Steuer oder eines Discounts. Die Berechnung basiert dabei vollständig auf den Parameter, die über das Microservices API übertragen werden. 

* **Basic persistence:** Dieser Microservice hat seine eigene, gekapselte Persistenz. Wenn die Daten in der Persistenz ändern, dann werden Events publiziert, die andere Services über die Änderung informieren. Der Persistenzmechanismus gehört dem Service und wird von den unterschiedlichen Service Instanzen gemeinsam genutzt. Dies erlaubt es den Service Implementationen zustandslos zu sein.  

* **Externalized persistence:** Dieser Microservice nutzt einen externen Service für die Persistenz. Dies könnte ein anderer Microservice mit Peristenzmöglichkieten sein, oder aber ein dedizierter Persistenzservice, der Teil der Platform Infrastruktur ist (z.B. eine NoSQL Datastore oder ein RDBMS). Wenn ein dedizierter Data Persistenz Service genutzt wird, ist es wichtig, dass dieser eine Isolation der Daten ermöglicht, die der Service besitzt.  

* **Command Query Responsibility Segregation (CQRS):** Diese Art von Microservice optimiert die Implementierung eines einzelnen Microservices auf unterschiedliche nicht-funktionale Anforderungen für das Read und Write Verhalten. Das Interface des Service ist aufgeteilt in Kommandos, die den Status von Daten verändern und Abfragen die nur lesend auf die Daten zugreifen. Dieses Pattern eignet sich vor allem dann, wenn es signifikante Unterschiede bei den Performance- bzw. Kapazitätsanforderungen zwischen lesenden und schreibenden Operationen gibt. Da die Service Implementation zweigeteilt ist, ist die Datenmodellierung, die unterliegende Persistenztechnologie und die Anzahl Instanzen für die Abfragen unabhängig von der Implementation der Kommandos, bzw. der schreibenden Operationen. 

* **Event handler:** Dieser Microcservice wird ausschliesslich durch einen Event im Event Hub getriggert. Skalierbarkeit wird über das Pattern "competing consumers" gegen eine gemeinsam genutzte Subscription erreicht. Der Microservice kann auch neue Event erzeugen und in den Event Hub publizieren, um andere Services über seinen Zustand zu informieren.


![Inner Architecture](image/ms-inner-architecture.png)

         


 