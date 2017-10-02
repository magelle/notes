# CQRS

## CQRS - command query responsability segregation

Séparer lecture et écriture de la couche d'accès à la base de données.

### Pourquoi ?

- Le volume de lecture est, la plupart du temps, très supérieur au volume d'écriture
- La forme des données est très différente entre l'écriture et les différentes lectures
- Les traitements sont aussi très différents (recherche, aggrégations, ...)

### Comment ?

- Du traitement des données au stockage, tout doit être découplé.
- Les données enregistrées arrive via la partie write et sont stockés dans la base write
- La (ou les) base(s) read "écoutent" la base write pour se mettre à jour
 - Queue de message
 - batch de mise à jour
- Les requêtes arrivent sur la partie write et accèdent aux données de celle-ci

### Avantages

- Les données peuvent être stockée comme elles seront affichées (traitement de la données à sa création et non à la lecture)
- Le support de stockage Read peut être adapté au besoin (base document, index de recherche, ...)
- Les traitement read / write sont séparés et ont donc une meilleur maintenabilité
- Read et write peuvent scaler de manière différente
- Les données de la base Read peuvent être reconstruites à partir de la base Write (Besoin évoluant, nouveau besoin)

### Inconvénients

- Lorsque Read et Write sont asynchrone (la mise à jour de Write provoque la mise à jour de Read "plus tard"), il faut gérer la 
cohérence à terme
- Read et Write peuvent diverger
- Le nombre de technos augmente (si base Read différente de Write)
- Le nombre de livrable augment (si livrable Read différent de Write)

### Cas d'usages

- E-commerce : Formulaire de mise en vente (Write), recherche (Read), page produit (Autre Read)
- Banque : ?

### Resources

- ?
