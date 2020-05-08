# Reactive architecture

## Seek isolation

### Types of isolations

#### State isolation

Always go through API to get data from another service.

No database sharing.

#### Space isolation

Always consider the other services are on another machine.

#### Time isolation

Communicate through asynchronous messages

#### Failure isolation

A failure should be isolated in a single service.

### Isolation techniques

#### Bulkheading

- create failure zone isolations
- failures will not propagate to other services

#### Circuit Breakers

- cut the circuit when the other service is under stress
- avoid retry when other service is overloaded
- quarantine failing service
- State : closed (normal) -> open (fail fast) -> half open

#### Message Driven Architecture

- Asynchronous non blocking messages
- isolate from failures
- services not dependent on the response

#### Autonomy

- Allow services to operate independently
- Allow stronger scalability and availability
- tolerate more failures
- Don't require other services to operate all the time
- Have enough info to resolve conflicts and repair failures
- only asynchronous messages
- enough internal state
- use eventual consistency
- avoid direct synchronous dependencies

#### Gateway services

- When client needs to call multiple APIs
- client request go through gateway service
- gateway service orchestrate calls and aggregate responses
- gateway service handle failures

## Consistency, Availability, and Scalability

- __Scalability__ : meet increasing demands, while remaining responsive.
- __Consistency__ : all members have the same view / state.

- __Availability__ : Remains responsive despite any failure.



- **Performance** is about **one** request when __scalability__ = optimize ability to handle load

#### Messages order problem

when several services receive messages in different order we can :

- Add information (sequence or timestamp for instance)
- Add another service to do a corum
- Merge states (CRDTs)
- give the responsability to one service instance (sharding) 

### Consistency

Information take time to be transfered. The receiver state may change before it receive the message.

Everything is eventual.

#### Eventual consistency

> In absence of new updates, access to a piece of data will eventually return the most recent data.

Different types :

- Eventual consistency
- Casual consistency
- Sequence consistency
- ...

#### Strong consistency

> An update to a data needs agreement from all nodes before it becomes visible.

A lock allow a system to simulate Strong consistency.

### Law of Scalability

#### Contention

- Single limited resource = competition to access
- Only one winner, others wait

**Amdahl's law** : 

> Defines the maximum improvement gained by parallel.
>
> Improvement from parallelization are limited to the code which can be parallelized.
>
> Contention limit parallelization and reduce the improvements.

#### Coherency delay

Time to synchronize all nodes.

More nodes = coherency delay increase

**Gunther's universal scalability law** :

> Coherency delay result in negative effect when we add nodes.
>
> Cost to coordinate nodes exceed benefits of adding nodes.

**Linear Scalability is unachievable**

Reactive systems reduce contention by :

- Isolating locks
- Eliminating transactions
- Avoid blocking operations

They mitigate coherency delays by :

- Embracing eventual consistency
- Building in autonomy

This allow for higher scalability

The goals is to reduce or eliminate the things that prevent scalability

### CAP Theorem

Distributed system cannot provide more than two of the three :

- Consistency
- Availability
- Partition tolerance

#### Partition

> System continue de operate despite an arbitrary number of message being dropped (or delay) by the network.

To avoid this we can :

- Sacrifice consistency (AP)
- Sacrifice availability (CP)

### Sharding

Isolate contention -> sharding

Sharding should occurred at application level

Sharding is :

- Partition entity (or actors) according to ids (or shard keys)
- group of entity = a shard
- each entity = one shard
- each shard = one location
- one location -> no distribution
- entity act as a consistency boundary

A coordinator route the traffic.

aggregate roots are good candidate for sharding.

Balancing shard :

- good key = randomized distribution
- common key : UUID, hashcode
- poor key -> hotspot

Aim for 10 times as many shards as you have nodes

#### Plus and cons

- does not eliminate contention but isolate it
- within a single entity there is contention
- router/coordinator is source of contention
- shared system minimize contention by
  - limit the amount of work done by the router / coordinator 
  - isolate contention to individual entities

- **Scalability** : distributing shards over more machines
- **Strong consistency** : isolate operations to a specific entity
- Sharding sacrifice availability
  - but can migrate to another nodes eventually

#### Caching and sharding

Each entity has its own cache. Sharding allow each entity to maintain cache consistency.

### CRDTs

Conflict-free Replicated Data Types

- On application level
- Highly available and eventually consistent
- data stored on multiple replicas
- Update are applied to one replica, then copied asynchronously
- updates are merge to get final state

#### Two types

- CvRDTs : Convergent Replicated Data Types
  - Copy states
  - require merge operation
    - Commutative
    - Associative
    - Idempotent
  - CvRDTS types
    - Sets, Registers, counters, maps, ...
- CmRDTs : Commutative Replicated Data types
  - Copy operations

#### Pros and Cons

- Data are stored in memory (should fit in it)
- Can be copied to disk
- Best for small data set, with infrequent updates

- Don't work with all data types (needs a merge function)
- Some complex merge may need tombstone
  - Tombstone is a marker that show something was deleted
  - Tombstone result in datatypes that only get larger
- may tweak write consistency to get more consistent, but it will cost availability

### Consistency of availability

- Business decision
- It's about balance

## Message Driven Architecture

Asynchronous and non blocking message.

messages are sent without waiting for the response.

#### Pros

- Resources a freed immediately

- Reduce contention -> potential higher scalability
- Messages can be queued for delivery in case the receiver is offline

### Cons

- In monolithic architecture, coordination and consensus is done through database transactions
- Long transactions means slow and brittle systems
- Needs for distributed transactions

### When to use synchronous messages

- Should be driven by domain requirements
- Use asynchronous by default
- Understand consequences of a choice

### Sagas

Represent a long running transaction

Multiples requests (in parallel or in sequences) are managed by a Saga.

When if fails :

- Run the compensating actions for all completed steps
- Then the Saga is failed
- if compensating action failed, it's needs idempotent.
- Compensating action may be executed before the request.

Timeouts

Possibilities :

- request failed.
- request succeed but response failed.
- request was queued and will succeed or failed eventually.

Compensating is not rollback

- Rollback: remove the evidence of transaction

- Compensating action : 
  - apply on top of previously completed actions
  - evidence of previous action remains

#### Moving forward with failure

Examples:

- Retries
- Fallback
- move failures to an error queue

### Messaging patterns

#### Two generals problem

- Two army generals try to coordinate an attack
- the messengers travel through th enemy territory, may be killed or captured
- We can never be 100% sure both are ready to attack

#### Guaranteeing delivery

Because of two general problem we can only send messages:

- At least once (may receive duplicates)
  - Require messages to be stored by the sender to enable retries
- At most once (may not be received)

At least once + idempotence = exactly once delivery

### Messaging patterns

#### Point to point messages

- each service depends on other service directly
- Services are directly coupled to each others
- Services knows and understand their dependencies
- Pros / Cons
  - Clear dependencies
  - Higher coupling
  - Complexity is more directly observable

#### Publish/subscribe

- Services publish messages to a message bus
- other services subscribe to the message
- Services does not know each others
- Services are coupled to message format
- Pros / Cons
  - Dependencies are more flexible
  - Coupling is lower
  - Complexity may be harder to see

## CQRS / ES

**Event sourcing** : capture the journey

- Ability to rewind

**Snapshot** : only when needed

#### Changing model in event sourced system

Integrity of the log is guarantee because it's append only.

How to handle model change ?

- Use event versioning
- Use only flexible format (Json, Protobuf)

**Write model** needs to be consistent

**Read models** don't need strong consistency

#### Cost

- More objects/classes
- May result in multiple datastores
- UI must be design to accept eventual consistent architecture
- Maintain support for old events format can be challenging
- May require more storage due to long event history and read data duplication
- Data duplication cav result in sync issues
  - Solved by rebuilding projections

