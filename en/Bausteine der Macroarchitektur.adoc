# Bausteine der Makroarchitektur

## Microservice Platform

### Config Store

## Service Routing

### Load Balancing

### Self Healing

### Auto Scale

### Microservice Execution

## Backing Services

### Persistence

#### RDBMS 

#### NoSQL

#### Object Store / Distributed File System (DFS)

#### Message Broker

#### Event Hub / Event Bus

An event bus is a conduit for the events generated. Typically they are backed by a messaging topic so that you get the publish subscribe semantics over this conduit.

#### Event Store

Event stores usually store changes applied to an entity. By replaying the changes, it is possible to resurrect the state of an entity to any point in history. Event stores may also make use of a database to store state change audit trails.

## Dev/Ops Automation

### Build Automation

### Test Automation

### Image Repository

### Deployment Automation

### Platform Automation


