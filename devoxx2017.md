# Retour de Devoxx2017

## Univers Devoxx
La devoxxFr, c'est plus de 2000 développeurs et plus de 200 speeker qui viennent apprendre et échanger autours de nombreuses technologies, outils et pratiques.
C'est donc beaucoup de monde qui se regroupe pour assister à des conférences, des ateliers et des quick talks peandant trois.
Cela fourmille donc de gens interessants et interessés.

## Rencontre dans le hall des expostants
La devoxxFr c'est d'abord les conférences et hands-on lab mais c'est aussi ses exposants qui vienent présenter leur outils et services.
C'est donc l'occasion d'en apprendre un peu plus sur un outils, de rencontrer les dévelopeurs des solutions que l'on utilise, d'en découvrir de nouvelles et de se tenir informer de l'évolution du marché foisonnant des outils.

### Elasticsearch
J'ai pu dicuter avec l'équipe Elasticsearch présente le mercredi. Pour rappel Elasticsearch est un index de recherche disposant d'une interface REST. Mais Elasticsearch n'est pas le seul produit qu'ils proposent. Kibana, logstash et beats font aussi parti des outils proposés. Logstash est un outils de parsing de logs. Il permet de récupérer des logs applicatifs, ou d'outils pour les parser, les enrichir et les envoyer vers une base de stockage, elasticsearch par exemple. Kibana vient ensuite requéter Elasticsearch pour créer des dashboards et des graphs permettant de visualiser ces logs, ou tout autre donnée présentent dans elasticsearch. Les Beats sont des agents spécialisés et ultra léger qui seront utilisé à la place de logstash pour récupérer des informations (logs ou autres). En effet logstash et un peu gourmant en resources, au contraire des Beats. Ces agents spécialisé (ils sont liés à un outils, apache par exemple) récupère les logs de vos outils pour les envoyés vers elasticsearch ou logstash (pour les enrichirs). Les Beats viennet aussi avec leur dashbord kibana c'est qui est très pratique lors de la première mise en place d'une stack elastic.
- cloudbees jenkins blueocean

- jfrog artifactory
- ikoula, clevercloud

## Université CQRS/ES
## Atelier CQRS/ES
## Javaslang
- mieux que java 8
- allant plus loin vers la programmation fonctionnelle
## JOOQ
- DSL pour vos requêtes
- généré à partir de la base de donénes
## rkt
- sécurité -> imaghes signées
- pas de daemon
