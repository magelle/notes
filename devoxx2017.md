# Retour de Devoxx2017

## Univers Devoxx
La devoxxFr, c'est plus de 2000 développeurs et plus de 200 speeker qui viennent apprendre et échanger autours de nombreuses technologies, outils et pratiques.
C'est donc beaucoup de monde qui se regroupe pour assister à des conférences, des ateliers et des quick talks peandant trois.
Cela fourmille donc de gens interessants et interessés.

## Rencontre dans le hall des expostants
La devoxxFr c'est d'abord les conférences et hands-on lab mais c'est aussi ses exposants qui vienent présenter leur outils et services.
C'est donc l'occasion d'en apprendre un peu plus sur un outils, de rencontrer les dévelopeurs des solutions que l'on utilise, d'en découvrir de nouvelles et de se tenir informer de l'évolution du marché foisonnant des outils.

### Elasticsearch
J'ai pu dicuter avec l'équipe Elasticsearch présente le mercredi. Pour rappel Elasticsearch est un index de recherche disposant d'une interface REST. Mais Elasticsearch n'est pas le seul produit qu'ils proposent. Kibana, logstash et beats font aussi parti des outils proposés. 

Logstash est un outils de parsing de logs. Il permet de récupérer des logs applicatifs, ou d'outils pour les parser, les enrichir et les envoyer vers une base de stockage, elasticsearch par exemple. 

Kibana vient ensuite requéter Elasticsearch pour créer des dashboards et des graphs permettant de visualiser ces logs, ou tout autre donnée présentent dans elasticsearch. 

Les Beats sont des agents spécialisés et ultra léger qui seront utilisé à la place de logstash pour récupérer des informations (logs ou autres). En effet logstash et un peu gourmant en resources, au contraire des Beats. Ces agents spécialisé (ils sont liés à un outils, apache par exemple) récupère les logs de vos outils pour les envoyés vers elasticsearch ou logstash (pour les enrichirs). Les Beats viennet aussi avec leur dashbord kibana c'est qui est très pratique lors de la première mise en place d'une stack elastic.

# Les conférences

### CQRS/ES
L'event sourcing, a été popularisé par Greg Young. L'idée par du constat que nous stockons dans les base de données, l'état courant de l'application. Ceci présente plusieurs problèmes dont deux principaux :
 - l'évolution des demandes métiers amène à revoir souvent le modèle de représentation cet état 
 - lors de la modification de l'état, nous perdons des informations importante : quel est ce changement, qui l'a demander, quel était l'état avant le changement.
Partant de ce constant l'event sourcing propose de ne plus stocker un état mais plutot d'enregistrer les évènement qui surviennent au sein du système. En stockant les évènement du système, il n'y a plus de modification du modèle de données, seulement de nouveaux évènements. Il devient également possible de récupérer une donnée à n'importe quel moment dans le temps en rejouant les évènements jusqu'à cette date. Pour récupérer l'état actuel d'une données, il faut récupérer tous les évènements ayant eu lieu sur cette données puis les rejouer dans l'ordre. Lorsque nous rejouons tous nos évènements dans notre système, nous créont une projection. Une projection est une représentation particulière de l'ensemble des évènements ayant eu lieu dans le système. Il est possible de créer différentes projections pour différents usages. Nous éliminont alors le problème de la représentation unique de l'état dans les systèmes classiques. Le modèle de données n'est souvent pas adapté à la représentation que nous souhaitons avoir. Une projection étant crée à partir de l'ensemble des évènements, en créer plusieurs est facile. 

Nous modifions donc notre système en créant des évènements mais nous récupérons les informations de celui-ci via les projections.

Cette séparation des parties command et query d'une application est un pattern d'achitecture appelé CQRS (Command Query responsability ségrégation). CQRS n'est pas apparue avec l'event sourcing, seulement, la complexité apporté par l'event sourcing peu être géré avec CQRS. Le pattern CQRS prend ses fondations dans un constat simple : Dans la plupart des systèmes il y a beaucoup plus d'écriture que d'écritures. Ces lectures ont également des formes plus variées. CQRS propose alors de séparer complètement votre applciation en deux : Une partie lecture et une partie écriture. Cette séparation ira jusqu'à la base de données. Les commandes écrirons donc sur un support différent de ceux auprès desquels la partie query ira chercher ses informations.

Bien sur, comme tout outils CQRS et EventSourcing sont des outils et non des Silver Bullets.

L'atelier CQRS/ES lors de la Devoxx a été l'occasion de mettre tout cela en pratique. Partant d'une base de code existante, nous avons ajouter nos propres gestion et création d'évènement ainsi que des projections spécifiques.
L'exercice est disponible ici : [https://github.com/DevLyon/mixter](https://github.com/DevLyon/mixter)

### Javaslang
Javaslang (renommé vavr depuis) est une librairie pour java. Son objectif est de rendre plus facile la programmation fonctionnel en Java et d'aller plus loin que Java 8. La présentation était l'occasion de voir comment l'utiliser.
La présentation est disponible ici : [https://www.youtube.com/watch?v=IIWWvvZn9SA](https://www.youtube.com/watch?v=IIWWvvZn9SA)

### JOOQ
En java, pour accéder à une base de donénes, deux solutions sont très utilisés : les ORM (Hibernate, Eclipse link, ..) et des requêtes SQL via JDBC. Cependant, ces deux techniques ont des inconvénients. Les ORM sont très bien adapté pour faire du CRUD (Create, Read, Update, Delete) simple mais ne sont pas à l'aise avec les requêtes complexes. De l'autre coté, l'utilisation du SQl via JDBC permet d'écrire toutes les requêtes SQL imaginable mais la maintenance en est douloureuse. Au renommage d'une table on doit repasser sur toutes les requêtes. Les requêtes SQL ne sont pas type safe.
JOOQ pour Java Object Oriented Query propose une librairie et des outils pour générer un DSL de votre base de données qui pourra être utiliser pour créer des requêtes. Les requêtes vers votre base de données deviennent donc type safe et la maintenance est facilité.
Voici un exemple d'écriture de requête : 
```java
create.selectFrom(BOOK)
      .where(BOOK.PUBLISHED_IN.eq(2011))
      .orderBy(BOOK.TITLE);
```
La présentation est disponible ici : [https://www.youtube.com/watch?v=Gev7iQ5_VCA](https://www.youtube.com/watch?v=Gev7iQ5_VCA)

