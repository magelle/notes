# Event sourcing

## C'est quoi ?
- Sauvegarder des évènements plutôt que l'état du système = ce qui a changé et pourquoi 
- Au besoin, l'état est reconstruit à partir des évènements
- Les évènements sont immutable (ils sont arrivés et ne peuvent être modifié ou supprimé)
- Ils sont l'unique source de vérité
- Event : dans le passé, une transition

## Pourquoi ?

- Le métier résonne plus souvent en terme d'évènements que d'état
- Piste d'audit gratuite
- permet de ne pas perdre d'information (lorsque l'état est modifié, on perd l'ancienne valeur)
- Ne pas perdre de données

## Comment ?
- Transaction script vs domain model
- Command sourcing vs event sourcing
- 

## Avantages
- Pas de perte de données
- Construction de vues spécialisées
- L'état peut être reconstruit à partir des évènements
- 

## Inconvénients
- Pattern peu utilisé
- Evolutivité du system faut-il modifier les évènements, quand ?
- Gérer l'idempotence
- Que faire si plusieurs évènement sont créés au même moment ?
- Géré l'ordre des évènements dans les systèmes asynchrones
- CQRS quasi obligatoire
- Gestion des systèmes distribués
- 

## Typical examples
- Compte bancaire = une suite d'opérations
- GPS tracking = une suite de position
- Systèmes de gestion de version
- 

## Tips and Tricks
- Snapshot
- l'état peut être la source principale de données
- Rendre le traitement des évènements d'un agregat synchrone
- généré les changements d'états concurrents avec le retry
- 
