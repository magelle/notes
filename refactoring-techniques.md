# Techniques de refactoring

## Stratégies de tests
La pyramide des tests : Tests unitaires > Tests d'intégrations (non régréssion) > Tests End to End / GUI
- les tests unitaires se charge de tester chaque composant assez profondément afin de vérifier que celui-ci fait ce que le développeur attend de lui.
- les tests d'intégrations permettent de vérifier que tous les composants fonctionnent correctement ensemble et qu'ils fonctionnent comme le veux le responssable fonctionnel
- les tests E2E / GUI sont souvent couteux à écrire et à maintenir. On prévilégira donc les chemins critiques pour vérifier que l'application est utilisable.

## Ajouter des tests
Sur un application legacy, deux stratégies (complémentaires) peuvent être employées : 
 - Créer un filet de tests End 2 End
  - souvent très couteux à mettre en place
  - permettent pouvoir faire du refactoring aggressif en remplacant de larges portins de code.
 - Ajotuer des tests unitaires et refactorer en douceur
  - Utiliser le safe refactoring
  - peut être frustrant (On revient plusieurs fois sur le code, on peut-être bloqué par des portions de code non testés)

## Safe refactoring
- Utiliser au maximum els capacités de l'IDE
- Le renommage (classe, méthode, variable)
 - Permet de clarifier le code et de le rendre plus expressif
 - Alt F6 sur IntelliJ
- Extract méthode
 - Découpe le code pour mieux le comprendre
 - Peut amener vers un extract delegate
- Extract delegate
 - Extract d'un méthode vers une autre classe
 - Répartie les responssabilités
 - Permet des tests unitaires plus facile
 - Ctrl + Alt + M (méthode) C (constante) V (variable) P (Paramètre)
- Créer des wrapper de méthodes statics
 - Permet de créer un mock partiel
 - Facilite le test
- Créer des wrapper de méthodes system (println)
 - Permet de créer un mock partiel
 - Facilite le test 

## Articles 
[Rewrite vs refatctoring 17 essential reads](https://techbeacon.com/app-dev-testing/rewrites-vs-refactoring-17-essential-reads-developers]

## Pour s'entrainer
- [Birthday greetings kata](https://github.com/xpmatteo/birthday-greetings-kata) 
- [Gilded roses kata](https://github.com/emilybache/GildedRose-Refactoring-Kata)
- Les kata de refactoring d'[Emily Bach](https://github.com/emilybache)



