# Functionnal Programming : 

## What is it ?
 - Programming with fuction
 - Lambda calculus
 - != language fonctionnel
 - Way of thinkning
 - Paradygme de programmation
 
## Fonction
 - Déclaration : f(x)
 - Application : f(2)
 - Substitution : f(2) = 3 (memoization)
 - Function = ensemble de départ (domain) -> ensemble d'arrivé (co-domain)

## Conception fonctionnelle
 - Coeur fonctionnel (pure)
 - à l'exterieur du coeur : les effets de bords
 - on va tendre vers cette architecture car on va essayer d'avoir le plus possible des fonctions "pure"
 
## Types de fonctions 
 - Total vs partiel
 - Total => renvoie un résultat
 - Partiel => renvoie une fonction
 - lambda = 
 - Functor = Type mapping between categories
 - Predicate = a function that is evalued to true or false
 - closure = fonction avec des variables non local (pas défini à l'intérieur)
 
## Opérations sur les fonctions
 - composition de fonction f(g(x)) => g o f = h

## Monads, Functor, Lenses, ...
### Data types
Define what is my value
- __Option__ : there may be a value
- __Either__ : there is aither this value (of this type) or that value (of this other type)
- __Try__: there is either this value (of this type) or this error (aka exception in kotlin)
- __Validated__: there is either a value (of this type) or an error of this type
- __Ior__ : there is maybe a value of this type or maybe a value of this other type or maybe both (values of types)
- __Id__ : There is this:)
- ...
### Type classes
Define what you can do with my value
- __Show__ : can be transformed to a string
- __Eq__ : can be compared
- __Order__ : can be compared
- __Functor__ : is able to transform the content of a higher kind
 - ex: Option, Try, ...
 - map : this is how you transform the existing content
 - lift : this is how you __will__ transform a content 
- ...
### Effects
- 
### Lenses
- 


## Tips to begin
 - https://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming
 - Il était une fois réduce
 
