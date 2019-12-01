# Domain Driven Design

Bei **Domain Driven Design** (oder kurz: DDD) handelt es sich um ein Set von Mustern und Best Practices für die Erstellung von Architekturdefinitionen. Die Grundidee bei einem solchen domänengetriebenen Entwurf ist es, die Problemdomäne immer weiter in ihre Teilbereiche, die sogenannten Subdomänen zu zerlegen. 

Dabei wird nicht, wischen Mikro- und Makro-Architektur unterschieden, sondern zwischen Strategic und Tactical Design. Diese Konzepte entsprechen nur im weiteren Sinne der Makro- (Strategic Design) bzw. Mikro-Architektur (Tactical Design). 



## Bounded Context



## Context Map

## Entity

## Value Object

## Aggregate


## Upstream / Downstream-Beziehungen



## Integration zwischen Bounded Contexts 

Egal wie gut die Trennung der einzelnen Kontexte und Subdomänen gelingt, um eine Integration derselben wird man in den meisten Fällen nicht umhinkommen. DDD definiert auch, auf welche Art und Weise diese Integration funktionieren kann und geht dabei in erster Linie auf die Bedeutung des Schnittstellenmodells für die Bounded Contexts ein. 

### Partnership

Im Zuge der nötigen Integration arbeiten Teams gemeinsam an demselben Ziel. Schnittstellen werden gleichberechtig gemeinsam festgelegt. 

### Shared Kernel

Beschreibt einen gemeinsamen Kern, den sich mehrere Bounded Contexts teilen. 

### Customer-Supplier

Bei Customer/Supplier ist der Supplier upstream und liefert die Informationen im Domänen-Modell. Der Customer ist downstream und nutzt die Informationen. Dennoch definiert der Customer, wie das Modell aussehen soll. 

### <a name="conformist"></a>Conformist

Conformist bedeutet, dass ein Bounded Context ein Domänenmodell von einem anderen Bounded Context einfach übernimmt. 

### Anticorruption Layer (ACL)

Beim Einsatz eines Anticorruption Layer enthält der Downstream Bounded Context eine Schicht, um das eigene Domänenmodell vom Modell des Upstream Bounded Context zu entkoppeln. Das ist insbesondere zusammen mit dem [Conformist](.#conformist) sinnvoll, um so ein eigenes, vom anderen Modell entkoppeltes Modell zu erstellen. 

### Open Host Service

Bedeutet, dass der Bounded Context eine generische Schnittstelle anbietet, mi der andere Bounded Contexts ihre eigene Integration implementieren können. Häufig findest sich dieses Pattern bei öffentlichen Schnittstellen im Internet, aber auch innerhalb eines Unternehmens ist dieses Pattern eine mögliche Alternative. 

### Published Language

Ist ein für all Bounded Contexts zugängliches Domänen-Modell. Das kann beispielsweise ein Standardformat wie EDIFACT für Transaktionen zwischen Firmen sein, aber auch ein eigenes Format ist möglich. 

### Separate Ways

Beim Separate Ways haben die Bounded Contexts keine Beziehung auf der Software Ebene, obwohl eine Beziehung denkbar wäre.

