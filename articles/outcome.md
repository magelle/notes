# Chercher les bénéfices

Dans les projets dans lequel j'ai travaillé, j'ai remarqué qu'on avait tendance à oublier quelque chose.
Pas seulement nous les développeurs mais aussi les responsables fonctionnels et le management. Nous sommes tellement pressés de réaliser les fonctionnalités demandées, tellement concentré sur les problématiques techniques ou fonctionnelles que nous en oublions pourquoi nous travaillons. Il arrive même que certains en arrivent à développer des fonctionnalités qui ne seront jamais utilisées.

Ce que nous oublions tous trop souvent est l'outcome. 

##  Outcome ?
Difficile à traduire vers le français, l'outcome c'est le bénéfice que l'on va retirer d'un nouveau développement, d'une nouvelle fonctionnalité voir même de la correction d'un bug. C'est l'impact que va avoir cette évolution sur les utilisateurs, pour l'entreprise.
On l'oppose généralement à l'output, se qui sera livré.
Généralement, comme nous travaillons dans des sociétés dont l’objectif est de gagner de l'argent, l'outcome final est de gagner plus d'argent.

Pour faire un parallèle avec le domaine de la programmation, l'outcome c'est rendre ce qui est implicite explicite. C'est exprimer le pourquoi de la fonctionnalité, son objectif et sa raison d'être. Comme dans le code, on va essayer d'expliciter ce que le code fait plutôt que juste écrire comment il le fait, l'outcome permet d'expliquer pourquoi cette fonctionnalité a été choisie et priorisée et ce qu'elle doit apporter.

## Générer de l'outcome
Cependant il y a plusieurs manières possible de faire gagner plus d'argent à une société à travers une application.
La première est de créer un nouveau business. En ajoutant de nouvelles fonctionnalités, on peut gérer de nouveaux produits, de nouveaux services et ainsi conquérir de nouveaux marchés.
AWS en est un bon exemple. A travers un nouveau logiciel, Amazon à pu vendre son expertise en gestion de parc de machines et ainsi se créer un nouveau business, en plus du E-commerce.
De nouvelles fonctionnalités peuvent aussi avoir un impact sur l'existant en simplifiant un logiciel, il est possible de faire gagner du temps aux utilisateurs. Ce temps pourra alors être réutilisé pour augmenter la cadence de travail et donc réduire les coûts. Ou alors pour améliorer la relation client et donc lui proposer des offres au plus prêt de ses besoins.
Au contraire en ajoutant de la souplesse et de nouvelles possibilités on pourra alors proposer des produits aux clients proches de la haute couture avec des produits hyper personnalisés.

Parfois, la somme de travail est telle que l'outcome espéré ne sera visible qu'au bout de mois de développement. On entre alors dans un tunnel dont il est difficile de bout avant la fin. Les bénéfices pécuniaires sont donc un horizon lointain. Cependant il y a d'autres types d'outcome que l'on peut rechercher pour être sur d'avancer dans la bonne direction. L'apprentissage en est un. Notamment technique, en effet on est souvent tenté de développer l’outil couche par couche découvrant les problématiques techniques de chaque couche au moment du développement de celle-ci. Il est donc souvent nécessaire de revenir sur le développement de la couche précédente pour régler les problèmes de communication et de représentation des données au moment où l'on tente de faire communiquer ces différents modules. Malheureusement cette période est bien souvent en fin de projet et provoque des retards imprévus.
Il est donc souvent plus judicieux de travailler sur des slices verticales plutôt qu'horizontales. On entrera alors immédiatement dans les problématiques de communications entre les différentes couches et modules. On sera alors à même d'apprendre plus rapidement quels types de contraintes techniques et fonctionnelles qui vont survenir durant le développement.

## Comment
Je sais ce que vous vous dites : "OK, c'est bien joli tout ça mais moi je suis développeur. Je code. Je vais pas voir l'utilisateur, je ne participe pas au recueil du besoin, la définition de la roadmap, ... En gros je n'ai aucun pouvoir sur ce sujet.".
Et bien vous avez raison. Sauf sur la dernière partie. L'outcome est un outil est utile quand il s'agit de communiquer autour d'une fonctionnalité, d'un développement. Lorsque que votre responsable fonctionnel ou po vous présenter une fonctionnalité demander lui pourquoi, puis pourquoi, puis pourquoi, ...
Parfois il ne saura pas, parfois vous répondra de manière incomplète. Mais plus vous demanderez plus il sera lui devrait s’intéresser au sujet et vous apporter des réponses complètes.
L'outcome est un outil étrange. Lorsque l'on commence à se demander quel impact va avoir cette fonctionnalité et ce qu'elle va apporter à l'entreprise les possibilités s'ouvrent. Lorsque l'on comprend le but recherché derrière une nouvelle fonction il est alors possible de challenger le besoin réel de la fonctionnalité. On peut alors proposer des solutions qui amènent le même impact à moindre coût. On peut aussi questionner l'utilité réelle de la fonctionnalité et donc éviter des coûts de développement finalement peu utilisé une fois livrée en production. On peut aussi, en comprenant la finalité, découvrir que la solution envisagée n'est qu'une solution de contournement à un problème mal identifié.
En effet parfois le métier, l'organisation, les produits ont évolués dans les faits ma pas dans le logiciel. On se retrouve alors avec des modèles (dans le code) "tordus" afin de répondre au besoin sans être tout à fait adapté. Souvent identifier un modèle inadapté et le refondre permet de simplifier l'application et de mieux répondre au réel besoin. On réussit alors à simplifier le logiciel et donc limiter l'apparition de bugs, proposer un modèle plus proche de la réalité et donc plus simple à appréhender (onboarding plus rapide) et à utiliser ainsi que potentiellement plus souple et moins sujet aux erreurs (d'utilisation, de développement).

L'outcome est aussi un outil précieux pour négocier. Rappelez-vous combien de fois on vous a dis "Cette fonctionnalité est très urgente,. Il faut livrer au plus vite". Sur certains projets, toutes les fonctionnalités sont urgentes, à faire ASAP, pour hier.
Mais demandez quel sera l'outcome perdu si la fonctionnalité n'est pas livrée. Combien d'argent va perdre l'entreprise si la livraison n'est pas faite le jour J. La plupart du temps personne ne sait. Et donc il n'y a peut-être pas d'urgence. Vois même une autre fonctionnalité est peut être plus urgente.
Certains argueront qu'il y a des fonctionnalités réglementaires, des deadlines incompressibles, des rendez-vous client à ne pas manquer. Et justement c'est là ou chercher l'outcome le plus grand, la fonctionnalité avec le plus fort impact est important.
Par exemple une nouvelle réglementation arrive et il faut vite la mettre en place. D'un autre côté une fonctionnalité était prévu pour un client important et il faut absolument lui livrer dans les temps. On est bien obligé de tout livrer dans les temps non ? On ne peut rien faire de plus !
Mais combien va perdre l’entreprise si la réglementation n'est pas en place ?
La règlement tation porte sur tous les produits ?
Peut-on faire le développement pour une majorité des cas pour réduire le risque d'amende ?
A combien se négocie ce contrat avec le client ?
Y a-t-il des fonctionnalités qui étaient plus importantes que d'autres ?
...
Nombres de question peuvent être posées et les poser a deux effets : 
 - Poser la question de la priorisation qui peut être faite de manière plus précise en prenant en compte le risque (en €)
 - Suggérer la livraison une fonctionnalité avec un impact fort sans gérer tous les cas à la marge.
Il est ainsi possible de rentrer dans une négociation factuelle et de sortir d'une opposition simple équipe de développement contre métier ou chacun reste sur ses positions.
	
