# Retour sur Socrates Fr 2017

Il y a une semaine, grâce à Novencia qui est partenaire de l'évènement, j'était à Socrates France.

Socrates est une non conférence. Au contraire de la Devoxx par exemple, les sujets ne sont pas prévu à l'avance et il n'y a pas de programme des présentations. Au contraire le format est celui de l'open space : chacun peut venir proposer de discuter autour d'un sujet qu'il maitrise, ou non.
Ce format un peu particulier permet plus d'échange et d'interaction.

Socrates c'est aussi un lieu : le chateau de Rochegude. Le lieu est magnifique, on en oublierait presque que l'on est pas en vacances. C'est aussi la nourriture, excellente.

## Programme

# Socrates, Késako
- 3 ème année
- non conférence -> open space


# Organisation, Lieu, Restauration, Chambres
- 


# Déroulement, ...
- Arrivée, 

# L'expérience Socrates
- Fruit Shop
- Kata Turn Over
- How to learn
- TDD BDD DDD
- 

Story telling -> le voyage, premier, deuxième, troisième jours, retour, discussion

Il y a une semaine, j'ai eu la chance d'aller à Socrates France grâce à Novencia qui est partenaire de lévènement.J'avais hâte d'y être, car on me l'a bien vendu : des développeurs de talent qui se regroupe pour discuter dans un chateau 4 étoiles avec un service au top.

Mais commençons au début. Pour commencer il faut se rendre sur le lieu car la Socrates ne se déroule ni à Paris ni dans une autre grande ville mais à Rochegude, près d'Orange dans la Drôme. Il faut donc prendre le TGV jusqu’à Orange ou Avignon. N’ayant pas fait attention, je prends ds billets pour Avignon (40 km) au lieu de les prendre pour Orange (12km) et j'embarque avec moi deux compères de fortune avec moi. Un autre nous rejoindra dans notre erreur. 

Nous sommes donc 4 à partir ce mercredi matin de Gare de Lyon. On achète à manger et c'est bientôt le départ. 2h40 de train c'est long. Cependant, lorsque l'on se retrouve au wagon bar entre développeurs passionnés ça passe beaucoup plus vite et nous arrivons à Avignon en un clin d’œil.
Arrivé à Avignon le taxi réservé par Houssam, l'organisateur, nous attend déjà. Il nous emmène en 35 petites minutes au Château de Rochegude.

Le château est effectivement très beau. C'est une ancienne forteresse transformée en résidence d'été à la renaissance, ça promet.
Notre chambre est également très belle, les propriétaires on réussit à garder son esprit d'époque sans pour autant sacrifier le confort.
Nous profitons du temps qui nous reste pour visiter le château, ses salons, ses galeries et sa terrasse. Je vous invite à regarder les photos sur leur site pour vous rendre compte de la beauté du lieu.

Viens l'heure du repas, on ne m'a pas menti, c'est très bon.

# Kata Turn Over

Xavier Detant nous a proposé de faire une expérience : Un Kata sensé montrer l'impact du turn over sur un projet. Voici ce que l'on a fait : tous autour d'une table, nous avions chacun 3 minutes pour ajouter notre pierre à l'édifice du projet en cours avant de passer le PC au suivant. Aucune communication autorisée entre les différents développeurs. Le sujet du kata était le Roman Number Kata dans lequel il faut écrire un nombre passé en paramètre en chiffres Romains. 
Le PC est passé de mains en mains et a fait plusieurs fois le tour de la table.
La première fois il m'a été assez facile de faire passer le test écris par le précédent, puis d'en écrire un autre.
Au second passage de l'ordinateur, je n'ai eu le temps de faire qu'un peu de refactoring, tout le reste des trois minutes ayant été englouti dans une tentative de compréhension du code écrit par mes compères.
Au troisième passage je ne comprends plus rien. Les trois minutes sont bien trop courtes pour me permettre de bien comprendre l'algorithme qui est en train d'être mis en place et je n'ai le temps que d'écrire un petit commentaire disant mon incompétence avant le passer la machine au prochain.
Au quatrième passe, surprise, le code a été refactorer. J'ignore qui a eu le courage de faire ça en trois minutes. Les tests sont tous au vert. j'écrit un test qui me semble plus compliqué que ceux déjà écrit, mais il passe. Je me contente donc de faire un petit refactoring.

Le kata est enfin terminé, il nous aura fallu plus d'une heure pour terminer ce kata. Le code est propre concis et la plupart d'entre nous a découvert une nouvelle manière de coder ce kata. C'est l'heure de la rétrospective.

Au final tout le monde est d'accord pour dire que comprendre le code et son évolution a été très compliqué. Certains disent même qu'ils n'ont jamais vraiment compris l'algorithme mais que, grâce aux tests mis en place, ils ont été capables d'ajouter du code sans pour autant tout casser. Pour ma part je me rends compte à quel point les gens autour de la table ont à cœur de faire des tests et du code propre. J'imagine aisément ce kata fait par des développeurs moins à cheval sur ces sujets et ça me rappelle quelques lignes de codes que j'ai déjà pu voir lors de mes missions.

Grâce à ce kata je comprends mieux l'impact sur Turn Over sur un projet. Un développeur arrive sur le projet. Il n'a peu de temps pour monter en compétence. Il se contente donc d'écrire un peu de code pour ajouter la fonctionnalité demandée. Il ne comprend pas bien comment tout s'articule mais ça semble fonctionner, il passe donc au ticket suivant. Un autre développeur arrive, lui aussi ajoute du code. Très vite le code devient cryptique, incompréhensible, incohérent et sans tests impossible de le réécrire en étant sûr de ne pas introduire de bug. Voici comment naît du code legacy.


# Kata Fruit Shop

C'est le samedi après midi, je me rend au kata de Guillaume Jambet. Il nous propose de faire le Fruit shop kata. Je ne le connais pas et j'ai hâte de la découvrir. J'arrive et m'installe dans la salle. Guillaume nous explique le kata. L'objectif est de faire un programme qui prendra des fruits dans le prompt de la ligne de commande puis donnera le prix du total. 

Ex : 
$ pomme
1
$ pomme
2
$ cerise
2.75

Mais ce n'est pas si simple. Le kata se passera en 6 itérations de 10 minutes chacunes. C'est Guillaume qui joue le role du client. Il répondra à nos questions et nous devront lui faire des démos.
On commence.
TDD oblige je commence par écrire un test, j'écris le code pour le faire passer puis je commence à refactorer. Mais c'est déjà la fin des 10 premières minutes. Guillaume fait le tour des équipes (baeucoup sont en pair) environ la moitié a du code fonctionnel. Moi je n'ai même pas commencer à faire l'interface ligne de commande.
La seconde itération commence. Il faut maintenant ajouter un réduction de 20 centimes pour deux lots de cerises achetés.
Je fini mon refactoring et j'attaque l'interface en ligne de commande. Je ne teste pas cette partie, ce serait compliqué et, comme j'ai découpé interface et code métier, le code est trivial (5 lignes).
J'ai maintenant terminé la première itération. 
Il faut vite ajouter la réduction pour finir l'itération deux. J'ajoute un test mais c'est déjà la fin de la deuxième itération.

Les itérations s'enchainent, Guillaume joue bien son rôle de client. Il nous met la pression, se moque gentilment de nous et reviens sur ses décisions (ça ne m'impacte pas, je suis toujours en retard).

Je continue d'ajouter des tests, de les faire passer puis de refactorer. Je passe beaucoup de temps sur le refactoring pour éviter d'avoir un code qui devient trop complexe. Peut être trop au goût de mon client. Cependant, au fur et à mesure, je rattrape mon retard. Et fini la sixième itération sans difficultée.

Fin de la sixième itération, tout le monde s'arrète. C'est l'heure de la rétro. Qui à fini ? Qui est content de sont code? Qui à utiliser un système de gestion de version? Qui a fait des tests ?
Au final environ la moitié des équipes a réussi à finir. La plupart ne sont pas content du code qu'ils ont produits.
Guillaume ayant noté l'avancé et chaque équipe à la fin de chaque itération, on remarque une chose étrange. Ceux qui avait une solution fonctionnant dés les premières itérations sont souvent ceux qui n'on pas réussi à terminer la sixième. Il n'ont pas pris le temps de refactorer et leur code est devenue inmaintenable très rapidement. 

Ce qui m'a frappé lors de ce kata c'est la facilité avec laquelles on peut se laisser emporter par l'urgence. A vouloir absolument faire satisfaire le commenditaire et lui apporter ce qu'il demande, on en oublie de penser à la pérèninité du projet et on peut se retrouver très vite, en moins d'une heure durant ce kata, avec du code que l'on ne maitrise plus et qui devient alors un fardeau pour le développeur aussi bien que pour le client.
J'ai également remarqué que ce qui m'a permis de terminer ce kata est le refactoring constant lors des développements. J'ai passer beaucoup de temps à refactorer mais ce temps investi a été très vite payant car il me permettais de faire évoluer le code beaucoup plus vite. Et finalement les tests ne sont qu'un moyen de facilité le refactoring du code. 


refactoring (test est un outils)
