# Interactive Driven Design
## By Sandro Mancuso

# Constat 
- MVC est mal compris
- Souvent le code métier est dans les controlers
- Le code métier n'est pas protégé

# Architecture globale
- core le domain métier et son infrastructure
- web la partie exposant le domain 
 
# Architecture du domain métier
- Action : points d'entrées
- Domain Service : Contient le code métier
- Repo : accès aux données (persistence) et envoie de message

![Interaction driven design architecture](https://github.com/magelle/notes/blob/master/interation-driven-design.png?raw=true)
