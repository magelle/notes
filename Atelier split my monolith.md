# Atelier split my monolyt

- Train management
- Business rules
- Database schémas
- Qui est owner de quelle données

## Affect data to a "domain"

it's hard

Then example of affectation

## Split now

shared kernel /!\

Modularité != Distribution

## Patterns de migration

### Bubble context

Extraction d'un module, le nouveau utilise la base du legacy

### Autonomous bubble - synchronous

le nouveau module utilise maintenant une api du legacy, il a sa propre base

(peut être une étape après Bubble context)

### Autonomous bubble - state streams

now communicate through messages

pas de message métier juste, "ça a changé"

### Autonomous bubble - events + APi

évènements métier "l'email a changé"

### Exposing legacy assets as service

Nouveau module send commands through API





