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
__Arrow-kt__ docs may help you : https://arrow-kt.io/docs/
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
Define what you can do with my value of a define type
- __Show__ : can be transformed to a string
- __Eq__ : can be compared
- __Order__ : can be compared
- __Semigroup__ : can combine two value of this type
- __Monoid__ : can can combine (like semigroup) plus there is a empty value (e.g. empty list)
- __Foldable__ : can combine all values in one
- __Functor__ : is able to transform the content of a higher kind
 - ex: Option, Try, ...
 - map : this is how you transform the existing content
 - lift : this is how you __will__ transform a content 
- ...
### Effects
Handle side effects
- __IO__ : handle io type side effects (network, database, ...)
- __Async__ : handle async type computation
- __Promise__: Handle something that will answer later
- __Effects__ : Use callback coding style
- ...
### Lenses
get data from data structure and update them without pain
- __Iso__ : express that two type are the same and how to pass from one to another
- __Lens__ : fast access (functional reference) to get and set values in data structure
- __Prism__ : get part of the structure in certain conditions (e.g. head for list : there may not be a value)
- __At__, __Index__ : fast access by index
- ...


## Tips to begin
 - https://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming
 - Il était une fois réduce
 
## From OOP

- Dependency injection : 
  - just do currryfication 
  - then partial application
  - pass function dependencies as parameter
  - https://fsharpforfunandprofit.com/posts/dependency-injection-1/
- Functionnal Design Pattern : https://fsharpforfunandprofit.com/fppatterns/

