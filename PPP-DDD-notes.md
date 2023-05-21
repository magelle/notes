# Patterns, Principles, and practices of Domain-Driven Design - Notes

## Integrate with legacy

- Can integrate with : 
  - through database
  - expositing as a service
  - Bubble context 

Integrating distributed bounded context
- Database
- Flat file
- RPC
- Messaging
- REST

## Bounded context integration

Architecture is SOA (Service Oriented Architecture).

One bounded context can contains several business components.

On business component can contains severaval components.

One component is ultimately a use case, named with the event is produce.

### Integration with Messaging

Message Bus is different then Message Broker. A broker is a centralized système, a message bus is decentralized.

Commands are not the same as events.

You should do "store-and-forward". when something go wrong you have to emit events to revert the situation.

When an action have to access to several services (database, external web services, ...) you have to break down the cal in several commant -> side effect -> event.
So that any error would be retry.

Building component diagram and container diagram help you understand the objectives.

Event bridge can be used to make two messages bus to communicate.

Messages should use versionning and be retro compatible.

### Integration with HTTP

RPC is possible but lack availability and fault tolerance.

REST make use of hypermedia links (HAL).

HTTP caches is used to reduce the number of calls.

HTTP integration enable the use of common and widely used technologies.

Atom Feed can be used to create an event store and poll events.

You should think about how to archive events.

Events should be versionned.

Fault tolerance require more work.

## DDD Tactical patterns

Patterns from __Enterprise Applications Patterns__ and __Design Patterns__ gof.

- Factories: build the business object
- Application services: orchestrate Factories, repositories and business object
- Entities: identified by id
- Value object: identified by values
- Aggregate: grappe of object, used only through the root
- Domain services: what can be in a business object
- Domain event: make to communicate changes
- event sourcing: store events not snapshot

### Value object
