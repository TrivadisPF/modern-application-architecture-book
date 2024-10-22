# Prinzipien des Software Entwurfs

Die in diesem Kapitel vorgestellten Prinzipien empfehle ich als Handlungsmaximen bei der Zerlegung von Software in ihre einzelnen Module. Es sollten dabei immer die Prinzipien im Vordergrund stehen und immer Vorzug vor dem Einsatz konkreter Pattern, Frameworks oder Technologien haben. Die folgenden Prinzipien gelten dabei sowohl im Mikro- als auch im Makro-Architekturbereich.

## Keep it Simple and Stupid (KISS)

Das KISS-Prinzip fordert, zu einem Problem eine möglichst einfache Lösung anzustreben. 

Beim Erstellen einer Architektur bzw. beim Bau einer Softwarelösung geht es darum, gerade so viel Komplexität wie nötig zu bauen, um die Anforderungen zu erfüllen. Dies bedeutet aber nicht, dass auf eine angemessene Modularisierung verzichtet werden muss. Die Architektur soll passend zu den aktuell bereits bekannten Anforderungen sein und immer flexibel genug für zukünftige Änderungen sein. Gerade in den Zeiten von agiler Software-Entwicklung ist die Flexibilität der Architektur natürlich besonders wichtig, damit die Architektur dies auch leisten kann, ist die Aufnahme der für die Architektur wichtigen Anforderungen über den nächsten Sprint hinaus besonders wichtig. 


Je einfacher ein System gebaut ist, desto flexibler wird es in Zukunft sein. Es sollte immer nach der angemessenen Komplexität für die Anforderungen gesucht werden. Vorweggenommene Lösungen bringen selber eine gewisse Komplexität mit sich, die später die Möglichkeit, die tatsächlichen Anforderungen umzusetzen, vielleicht sogar einschränken wird!

* **You ain't Gonna Need It (YAGI):** Die Verlockung ist gross, Anforderungen, mit denen man als Architekt bereits rechnet, welche aber noch nicht definitiv sind, in der Architekturdefinition vorwegzunehmen.

* **Unnötige Abstraktionen:** Eine häufig anzutreffende Verletzung des YAGNI-Prinzips stellen überflüssige Abstraktionen dar.

* **Das Prinzip des letzten noch vernünftigen Moments für Entscheidungen**


## Don’t Repeat Yourself (DRY)
Natürlich möchte jeder seinen Code so frei wie möglich von Redundanzen haben. Es klingt zunächst einmal so, als müsste es das oberste Ziel jeder Architektur sein, Funktionalität möglichst gut zu kapseln, um sie später, wenn möglich gut wiederverwenden zu können. Tatsache ist aber, dass man es damit auch übertreiben kann. 

## Information Hiding Principle
Auch bekannt als: **Prinzip der Kapselung** bzw. **Encapsulation**

Das Prinzip des **Information Hiding** besagt, dass ein Benutzer einer Komponente möglichst wenig über diese wissen sollte. Merkmale, welche zur Verwendung einer Komponente nicht nötig sind, sollten vor den Benutzern verborgen bleiben. Der Grund dafür ist einfach: Alle Eigenschaften einer Komponente, welche nicht öffentlich zugänglich sind, sind auch in Zukunft einfach änderbar, weil Sie dann die Garantie haben, keine Abstimmungsaufwände betreiben zu müssen, und es keinerlei Folgeaufwände in benutzenden Komponenten nach sich ziehen wird. Wenn ein Aspekt für die Außenwelt unsichtbar bleibt, dann haben Sie die Garantie, dass sich keinerlei Abhängigkeiten zu diesem unbekannten Aspekt entwickeln. Das darf wirklich niemals unterschätzt werden! Nehmen wir einmal an, Sie schreiben Code, welcher zu einem x-beliebigen Zeitpunkt über die Position eines Planeten Auskunft geben kann, und das zurzeit von Sir Isaac Newton. Sie entwickeln einige Java-Klassen und geben diese in ein und dasselbe Package.

## Open Closed Principle
Das **Open-Closed-Prinzip** besagt, dass ein System immer offen für Erweiterungen sein soll, aber für Änderungen geschlossen. Vereinfacht gesagt bedeutet dies, dass es möglichst einfach sein soll, einem System neue Funktionalität hinzuzufügen. Und das möglichst ohne große Änderungen in der bestehenden Lösung. Wenn man dazu eine neue Klasse erstellen muss, ist dies nichts ungewöhnliches, wenn jedoch viele bestehende Klassen geändert werden müssen, dann wäre dies ein Indiz, dass das Prinzip verletzt wurde.

## Lose Koppelung

Keine Frage, egal wie gut man einen Architekturplan hinbekommt, es wird zwangsläufig zu Abhängigkeiten zwischen den einzelnen Bausteinen kommen. Einfach weil die einzelnen Features und Bausteine eines gesamten Systems nicht völlig isoliert voneinander existieren können. Bei der Festlegung einer solchen Verbindung zweier Bausteine, Kopplung genannt, ist es immer empfehlenswert, dies auf möglichst leichtgewichtige Art und Weise zu tun. Dabei kann dies einerseits bedeuten, tendenziell eine eher geringe Anzahl solcher Verbindungen zu haben, andererseits aber auch, dass im Zuge dieser Abhängigkeiten eine Komponente möglichst wenige Annahmen von der anderen Komponente treffen sollte.

## Hohe Kohäsion

Innerhalb einer Komponente ist es natürlich nichts Schlechtes, wenn es zu Dependencies der einzelnen Subbausteine kommt. Im Gegenteil, dies ist ein Indiz dafür, dass die Abgrenzung einer Komponente gegen den Rest des Systems an den richtigen Stellen gemacht wurde. Wenn Sie dies gut und ausgewogen hinbekommen, so spricht man von einer hohen Kohäsion oder Zusammengehörigkeit der Subbestandteile eines Bausteins. Bei Kohäsion geht es also um Abhängigkeiten bzw. Kopplung innerhalb gewisser Bausteingrenzen. Hier ist es dann natürlich auch nicht unüblich, wenn es zu enger Kopplung kommt.

## Separation Of Concerns

Auch bekannt als bzw. eng verwandt mit:
 * Single Responsibility Principle: Jeder Komponente wird nur genau eine Aufgabe zu Teil, womit es für jede Komponente nur genau einen Grund geben sollte, diese zu ändern [Mar02].
 * Prinzip der Modularität

Separation of Concerns, zu Deutsch etwa Trennung der Angelegenheiten, ist ein Prinzip, welches versucht, eine Vorgabe für jede Art der Modularisierung zu definieren. Es besagt, dass jede Angelegenheit von einem eigenen, dafür zuständigen Baustein abgebildet werden soll. Die einzelnen Aufgaben sollten also nicht x-beliebig auf die Systemstruktur verteilt sein.

## Hierarchischer Aufbau

## SOLID Principles

Bei den sogenannten SOLID-Prinzipien, welche von Robert C. Martin [Mar13] definiert wurden, handelt es sich um die aus seiner Sicht obersten Handlungsprinzipien, nach denen objektorientierte Software gebaut werden sollte. Jeder Buchstabe steht dabei für eines dieser fünf Prinzipien. 

* Single Responsibility Principle
* Open / Closed 
* Liskovsches Substitutionsprinzip
* Interface Segregation Principle
* Dependency Inversion Principle

### Liskovsches Substitutionsprinzip

Auch bekannt als: *Ersetzbarkeitsprinzip*

Einsatz: Mikroarchitekur

Eines der grundlegenden Prinzipien der objektorientierten Programmierung ist das der Vererbung. Eine sogenannte Unterklasse erbt dabei von einer Oberklasse sämtliche Methoden und Eigenschaften. Es können dabei sowohl neue Methoden und Eigenschaften hinzugefügt als auch geerbte Methoden abgeändert werden. Das **Liskovsche Substitutionsprinzip** besagt nun, dass eine andere Klasse, welche eine dieser Oberklassen benützt, ebenso korrekt mit einer der von ihr abgeleiteten Unterklassen funktionieren muss. Ist dies für eine abgeleitete Unterklasse nicht der Fall, so würde durch selbige dieses Prinzip verletzt sein. Würde also eine solche Unterklasse eine Methode überschreiben, sodass diese etwas fundamental anderes macht als die Oberklasse, wäre das nicht im Sinne des Konzepts der Vererbung. 

### Interface Segregation Principle
Auch bekannt als: *Schnittstellenaufteilungsprinzip*


Dieses Prinzip besagt, dass eine Komponente, welche Funktionalitäten als Schnittstelle für andere Komponenten zur Verfügung stellt, dies nicht in einer generellen Schnittstelle tun sollte, sondern diese in ihre einzelnen Zuständigkeiten aufzuteilen hat.

Durch die Anwendung dieses Prinzips ergeben sich folgende Vorteile:

* Der Provider der Schnittstelle ist einfacher auszuwechseln bzw. aufzuteilen.
* Die Art der Beziehung zwischen Anbieter und Benutzer einer Schnittstelle wird trans parenter.
­* Die Schnittstelle ist dadurch selbsterklärender und benötigt weniger zusätzliche Doku mentation.

Es geht wohlgemerkt also dabei nicht darum, für jeden Consumer eine eigene API zur Verfügung zu stellen, sondern vielmehr die API ganz ähnlich dem Separation-of-Concerns-Prinzips aufzuteilen.

### Dependency Inversion Principle

Beim Dependency Inversion Principle geht es um die Abhängigkeit zwischen Klassen, aber auch Komponenten höherer Hierarchieebenen. Es besagt, dass es unter gewissen Umständen Sinn machen kann, wenn die Beziehung eines Consumers einer Schnittstelle zum Provider über ein abstraktes Interface hergestellt wird. 

Es gibt dann keine direkte Abhängigkeit mehr vom Consumer zum Provider. Stattdessen gibt es eine Abhängigkeit beider zum explizit eigens definierten Vertrag, welcher sie miteinander verbindet. 

Dies darf keineswegs so verstanden werden, dass es prinzipiell für jede Beziehung zwischen zwei Komponenten eine solche Abstraktion geben soll. Vielmehr ist dieser Ansatz dazu gedacht, Abhängigkeiten zwischen Modulen, also Strukturen höherer Hierarchieebenen, zu steuern. So kann man durch Anwendung dieses Prinzips zyklische Abhängigkeiten vermeiden. Ein zweiter Effekt einer solchen Abstraktion ist, dass es dadurch möglich wird, alternative Implementierungen des Providers zur Verfügung zu stellen.

## Dependency Injection

Der Begriff Dependency Injection wurde von Martin Fowler 2004 geprägt. Zu dieser Zeit waren gerade jede Menge Tools wie das Spring-Framework in der Entstehung, deren Paradigma damals noch als „Inversion of Control“ bezeichnet wurde. Dies war Fowler zu generisch und er wollte für das Pattern, welches von diesen Werkzeugen implementiert wurde, einen passenderen und spezifischeren Terminus einführen. Eine Inversion of Control findet schließlich bei jeder Art von Framework statt, wo eine wiederverwendbare Komponente die Steuerung des Programmflusses übernimmt. Man liefert selbst die Implementierung dieser einzelnen Schritte an, den Ablauf aber gibt das Framework vor. Dependency Injection dagegen tut weniger als das bzw. etwas anderes. Es geht dabei darum, einem Consumer die konkrete Implementierung des Providers zur Verfügung zu stellen. 

Der jeweilige Consumer muss dann nicht mehr wissen, wie er zu einer solchen ProviderImplementierung kommt und wie diese erzeugt wird. Es führt also zu einer loseren Kopplung beim Zusammenspiel zweier Komponenten und kann daher ein wichtiges Werkzeug bei der Erreichung eines modularen Designs sein.

## Law of Demeter
auch bekannt als: *Principle of Least Knowledge*

Beim Gesetz von Demeter handelt es sich um einen Spezialfall des Information Hiding Prinzips bzw. der losen Kopplung. Dabei geht es darum, dass für den Consumer einer Schnittstelle das Zusammenspiel des Providers mit anderen Komponenten so gut es geht verborgen sein sollte. Der Consumer sollte dadurch möglichst keine Abhängigkeiten zu den vom Provider verwendeten weiteren Komponenten haben.

## Composition over Inheritance

Vererbung stellt zwar ein zentrales Konzept der Objektorientierten Programmierung dar, bringt aber auch eine ganze Reihe von Nachteilen mit sich. Sobald eine Unterklasse von einer Oberklasse erbt, bekommt sie durch diese Ableitung sämtliche Methoden und Eigenschaften der Oberklasse, ohne dass diese in der Unterklasse für den Developer noch sichtbar wären. Änderungen an einer Oberklasse wirken sich direkt auf die Unterklasse aus, ohne dass es überhaupt zu einer Adaptierung einer Schnittstelle gekommen wäre. Eine Vererbung ist also keine besonders transparente Form der Interaktion bzw. Wiederverwendung und ist darüber hinaus bedenklich, was die Umsetzung des Information-Hiding-Prinzips angeht.

Aus diesen Gründen sollte man immer versuchen, auf einfache Muster der Wiederverwendung zu setzen und nur in Anwendungsfällen, welche klar für Vererbung sprechen, diese auch einzusetzen. In Java kann man eine Klasse entweder gezielt als abstrakte Oberklasse zur Vererbung zur Verfügung stellen oder aber dies mit dem Schlüsselwort final gezielt zu unterbinden. Das Pattern, welches die allermeisten Vererbungen überflüssig macht, ist übrigens der Decorator.

## Design by Contract

Auch bekannt als: Programming by Contract

Design by Contract ist ein Konzept zur näheren Spezifikation der Schnittstellen einzelner Komponenten [Mey86], wobei das Ziel darin besteht, deren fehlerfreies Zusammenspiel zu fördern. Dabei werden die folgenden Dinge näher spezifiziert, welche an der rein statischen Definition der Schnittstelle nicht ersichtlich sind:

* Vor- und Nachbedingungen (preconditions und postconditions)
* Invarianten (invariants)

