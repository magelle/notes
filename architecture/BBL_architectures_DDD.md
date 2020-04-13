# BBL du 16/12/2016 Architectures DDD

* Keywords
  * CQRS
  * DDD
  * Architecture

* L'application est découpée en deux parties
  * Command et Query
  * Une couche application vient gérer l'ensemble
  
### Partie Command
  * Les commandes sont de simples DTOs
  * La commande est envoyée dans un bus de commande
    * Le bus de commande peut contenir plusieurs couches
      * Vérification simpliste de la commande (types de données, ...)
      * Gestion des transactions BDD
      * ...
    * la dernière étape du bus de commande est le dispatcher qui fait correspondre un commandHandler à la command
    * le commandHandler exécute la commande en utilisant le domain
    
* Le domain
  * entity : son identité n'est pas représenté par ses valeurs mais par un id (ex une personne, une voiture)
    * l'id est généré par le domain pas par la bdd, c'est un id métier de préférence
  * value object : son identité est représenté par ses valeurs
  * une entity peut être un value object dans un autre domain
  * aggregate
    * regroupe des entity et value objects
    * est souvent une entity
  * aggregate root : pilote l'ensemble des entities, value objecte et aggregatee du domain
    * toutes les modifications du domain passent par lui
  * Repository
    * Interface
    * N'agit que sur un aggregate root
    * ne contient que save (upsert), update, delete
  * Factory / mapper
    * Utiliser pour construire les objets du domain qui viennent du repository ou d'un autre domain
    * Vérifie que l'aggregate construit est cohérent
  
  * /!\ Si un objet a plusieurs comportement, il y a peut être plusieurs domaines (ex : un produit en logistique et facturation)
  
  * Shared kernel
    * Regroupe tous les objets transverse aux domaines
    * /!\ faire très attention en ajoutant des objets dedans c'est peut être une grosse bétise
    
 * Stockage
   * la partie commande stock de manière "key -> value" un objet sérialisé (en base SQL ou noSQL)
     * utilisation simpliste
     * pas de problème de modification du modèle de données
   * est dénormalisé dans d'autres bases pour la lecture (transfert de l'aggregate root)
   * peut être en event sourcing mais ce n'est pas obligatoire

* Deux "domaines" ou hexagones communiquent par objets sérialisés (JSON)
  * évite les effets de bord sur l'objet (pas de trasnfert de références)
  * permet le déployement en micro services si necessaire
  * un mapper est utilisé pour transformer l'objet sérialisé en objet du domaine

### Partie Query
* utilise des bases de données spécifiques (redis, ElasticSearch, ...)
* peut être reconstruit à partir de la base du domain
* peut être initialisé au démarrage de l'application

### Schémas
![](http://blog.octo.com/wp-content/uploads/2012/05/archi-21.png "Shémas architecture DDD")

### Souvenirs
![](https://pbs.twimg.com/media/CzzGy6iXUAAlcN5.jpg:large "Communication des domaines")
![](https://pbs.twimg.com/media/CzzHY8cXUAACa8n.jpg:large "Architecture")
