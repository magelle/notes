# Kata Ideas

Here are some ideas of not so obvious kata.

A code kata is an exercise in programming which helps programmers hone their skills through practice and repetition. 

The goal here is to propose some kata with, as a contraint, a design pattern, an architecture or a specific code style / paradigm.

## Bank Account Kata event sourced with Kotlin actor model
- Kotlin actors : https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.channels/actor.html
- Each agregate is an actor
- Each projection is an actor as well
- do all the pipes (command bus and commande router, event bus and router, agregate registry, ...)

## A Tennis Kata with state machine design pattern
- a simple tennis kata
- But each level of the game (game, set, exchange) is a state machine.

## A kata to try the greg young way of doing event sourcing : without agregate

- Try a local [eventstore](https://eventstore.com/)
- Subject to define, can be the subject of [eventmodeling.org](https://eventmodeling.org/)

## Trading Card Game Kata

[Trading Card Game](https://codingdojo.org/kata/TradingCardGame/)

## Big projects or architecture / DDD Kata

- Auction
- Activity report
- Train Trip kata

