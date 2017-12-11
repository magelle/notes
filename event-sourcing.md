# Event sourcing

## C'est quoi ?
- Sauvegarder des évènements plutôt que l'état du système = ce qui a changé et pourquoi 
- Au besoin, l'état est reconstruit à partir des évènements
- Les évènements sont immutable (ils sont arrivés et ne peuvent être modifié ou supprimé)
- Ils sont l'unique source de vérité
- 

## Pourquoi ?

- Le métier résonne plus souvent en terme d'évènements que d'état
- Piste d'audit gratuite
- permet de ne pas perdre d'information (lorsque l'état est modifié, on perd l'ancienne valeur)
- 

## Comment ?


## Avantages
- Pas de perte de données
- Construction de vues spécialisées
- L'état peut être reconstruit à partir des évènements

## Inconvénients
- Pattern peu utilisé
- Evolutivité du system faut-il modifier les évènements, quand ?
- Gérer l'idempotence
- Que faire si plusieurs évènement sont créés au même moment ?

## Typical examples
- Compte bancaire = une suite d'opérations
- GPS tracking = une suite de position
- 
