# Property base testing

Notes from reading of "Property based Testing with PropEr, Erlang, and Elixir

## Writing Properties

### Bad practices

Beware to not re-implement the function you want to test in the test itself.
Otherwise there is no way to know if the implementation is right.

### Modeling

Test your production code against a model.
This model can be a not optimized version of the alogrithme.
It should be __obviouly correct__.

Example of a good way to test the max function (which return the max of a list) : ```List.last(Enum.sort(list))```

Can also be used for Intergation tests of a system with a lot of side effects when how it's done is complex but how the user perceives it is simple.
A database for example.

Can also use a Oracle (a proved to be right example).
Maybe from another langage.

### Generalisation from examples

Find properties by generalizing a standard unit test.
Simply replace the examples by a generator.

```
forall {list, known_last} <- {list(number()), number()} ​do​
​    known_list = list ++ [known_last]
​    assert known_last == List.last(known_list)
​​end​
```

### Invariants

Example of invariant : 
- A store cannot sell more items than it has in stock.
- In a binary search tree, the left child is smaller and the right child is greater than their parent’s value.
- Once you insert a record in a database, you should be able to read it back and not see it as missing.

Most of the time one invariant will not be enought to be sure everything works perfectly.
But as you had other, you will get more and more confident about your piece of code.

Example: I want to test a sort function.

I could have a first invariant : each element of the list is greater than or equal to it predecessor.
but this is not enough and we could had :
- The sorted and unsorted lists should both have the same size.
- Any element in the sorted list has to have its equivalent in the unsorted list (no element added).
- Any element in the unsorted list has to have its equivalent in the sorted list (no element dropped).

### Symmetric properties

We tests several part of a system which has a symmetry.
It can be a direct symetry (encode / decode) or a less direct one (send message to a server, then to another, then to the first one).

Example of symmetric properties :
- encoder decoder
- reversable chain of operation: edit text and undoing changes
- translating french to english, to ... and back
- ...

Exemple :

```
forall data <- list({atom(), any()}) ​do​
	encoded = encode(data)
	is_binary(encoded) ​and​ data == decode(encoded)
​end​
```
is_binary test that the data is actually encoded

## Writing Generators

Some times you'll need a generator which create a wide area of values. Sometimes you'll need to generate a more specific set of values.

### Collecting statistics

In order to know wether or not the generated data are relevante, you can collect statistics arround it.

Example of generated statistics :
```
OK: Passed 100 test(s).
​ 	
​95% {dupes,{0,5}}
​5% {dupes,{5,10}}
```

### Simple custom generator

#### Resizing generator

You can tweak the existing generators so it better suits your needs.
For instance if your generated integer, you may want to have the generator create smaller or larger integer.
Here statistics are really useful to know what kind of data are generated.
This is possible by resizing the generator.

Beware, doing so may reduce the variability of the generated test cases.

Example :

```
property ​"​​profile 1"​, [​:verbose​] ​do​
​  forall profile <- [
​           ​name:​ resize(10, utf8()),
​           ​age:​ pos_integer(),
​           ​bio:​ resize(350, utf8())
​         ] ​do​
​    name_len = to_range(10, String.length(profile[​:name​]))
​    bio_len = to_range(300, String.length(profile[​:bio​]))
​    aggregate(true, ​name:​ name_len, ​bio:​ bio_len)
​  ​end​
​​end​
```


#### Transform Generator

You can create generators from other generators.
This garanty that no data generation will be done in the property and that your generator will be reusable.

```
​property ​"​​queue with let macro"​ ​do​
​  forall q <- queue() ​do​
​    ​:queue​.is_queue(q)
​  ​end​
​​end​
​
​​def​ queue() ​do​
​  let list <- list({term(), term()}) ​do​
​    ​:queue​.from_list(list)
​  ​end​
​​end​
```

#### Generation restriction

Sometimes we want to avoid some ranges of values (aka counter examples) to be given by the generator.
This is possible by restricting the generated values.

Sometimes it's possible to generate de values either with restriction or transformation :

```
// With restriction
​def​ even(), ​do​: such_that n <- integer(), ​when​: rem(n, 2) == 0
def​ uneven(), ​do​: such_that n <- integer(), ​when​: rem(n, 2) != 0

// With transformation
​​def​ even(), ​do​: let n <- integer(), ​do​: n * 2
​def​ uneven(), ​do​: let n <- integer(), ​do​: n * 2 + 1
```
In that case it is preferable to use transformation as it will be faster.

#### Changing probabilities

it is also possible to create a generator by specifying the frequences of several set of values.

Example :

```
def​ text_like() ​do​
​  let l <-
​        list(
​          frequency([
​            {80, range(​?a​, ​?z​)},
​            {10, ​?​\s},
​            {1, ​?​\n},
​            {1, oneof([​?.​, ​?-​, ​?!​, ​??​, ​?,​])},
​            {1, range(​?0​, ​?9​)}
​          ])
​        ) ​do​
​    to_string(l)
​  ​end​
​​end​
```

This text generator with create strings with less punctuation and more characters. 
In the way a actual text could be.

### More fancy generators

- Recursive generator : create a generator which is aware of what it is creating
- Symbolic calls : to ease debug

## Property base testing in practical

The property base testing does remplace all unit and integration testing.
Doing so would lead to complicated tests and missing points

For instance Unit Tests are a good way to store not trivial regressions to avoid it to come back (and document it).

Sometimes, brute force is a good solution.

