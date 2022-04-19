# List

Purely-functional, singly-linked lists.

## List

``` motoko
type List<T> = ?(T, List<T>)
```

## nil

``` motoko
func nil<T>() : List<T>
```

Create an empty list.

## isNil

``` motoko
func isNil<T>(l : List<T>) : Bool
```

Check whether a list is empty and return true if the list is empty.

## push

``` motoko
func push<T>(x : T, l : List<T>) : List<T>
```

Construct a list by pre-pending a value. This function is similar to a `list.cons(item)` function.

## last

``` motoko
func last<T>(l : List<T>) : ?T
```

Return the last element of the list, if present.

## pop

``` motoko
func pop<T>(l : List<T>) : (?T, List<T>)
```

Treat the list as a stack. This function combines the `head` and (non-failing) `tail` operations into one operation.

## size

``` motoko
func size<T>(l : List<T>) : Nat
```

Return the length of the list.

## get

``` motoko
func get<T>(l : List<T>, n : Nat) : ?T
```

Access any item in a list, zero-based.

<div class="note">

Indexing into a list is a linear operation, and usually an indication that a list might not be the best data structure to use.

</div>

## reverse

``` motoko
func reverse<T>(l : List<T>) : List<T>
```

Reverses the list

## iterate

``` motoko
func iterate<T>(l : List<T>, f : T -> ())
```

Call the given function with each list element in turn.

This function is equivalent to the `app` function in Standard ML Basis, and the `iter` function in OCaml.

## map

``` motoko
func map<T, S>(l : List<T>, f : T -> S) : List<S>
```

Call the given function on each list element and collect the results in a new list.

## filter

``` motoko
func filter<T>(l : List<T>, f : T -> Bool) : List<T>
```

Create a new list with only those elements of the original list for which the given function (often called the *predicate*) returns true.

## partition

``` motoko
func partition<T>(l : List<T>, f : T -> Bool) : (List<T>, List<T>)
```

Create two new lists from the results of a given function (`f`). The first list only includes the elements for which the given function `f` returns true and the second list only includes the elements for which the function returns false.

## mapFilter

``` motoko
func mapFilter<T, S>(l : List<T>, f : T -> ?S) : List<S>
```

Call the given function on each list element, and collect the non-null results in a new list.

## mapResult

``` motoko
func mapResult<A, R, E>(xs : List<A>, f : A -> Result.Result<R, E>) : Result.Result<List<R>, E>
```

Maps a Result-returning function over a List and returns either the first error or a list of successful values.

## append

``` motoko
func append<T>(l : List<T>, m : List<T>) : List<T>
```

Append the elements from one list to another list.

## flatten

``` motoko
func flatten<T>(l : List<List<T>>) : List<T>
```

Concatenate a list of lists.

In some languages, this operation is also known as a `list join`.

## take

``` motoko
func take<T>(l : List<T>, n : Nat) : List<T>
```

Returns the first `n` elements of the given list. If the given list has fewer than `n` elements, this function returns a copy of the full input list.

## drop

``` motoko
func drop<T>(l : List<T>, n : Nat) : List<T>
```

Drop the first `n` elements from the given list.

## foldLeft

``` motoko
func foldLeft<T, S>(l : List<T>, a : S, f : (S, T) -> S) : S
```

Fold the list left-to-right using the given function (`f`).

## foldRight

``` motoko
func foldRight<T, S>(l : List<T>, a : S, f : (T, S) -> S) : S
```

Fold the list right-to-left using the given function (`f`).

## find

``` motoko
func find<T>(l : List<T>, f : T -> Bool) : ?T
```

Return the first element for which the given predicate `f` is true, if such an element exists.

## some

``` motoko
func some<T>(l : List<T>, f : T -> Bool) : Bool
```

Return true if there exists a list element for which the given predicate `f` is true.

## all

``` motoko
func all<T>(l : List<T>, f : T -> Bool) : Bool
```

Return true if the given predicate `f` is true for all list elements.

## merge

``` motoko
func merge<T>(l1 : List<T>, l2 : List<T>, lte : (T, T) -> Bool) : List<T>
```

Merge two ordered lists into a single ordered list. This function requires both list to be ordered as specified by the given relation `lte`.

## compare

``` motoko
func compare<T>(l1 : List<T>, l2 : List<T>, compElm : (T, T) -> Order.Order) : Order.Order
```

Compare two lists using lexicographic ordering specified by the given relation `lte`.

## equal

``` motoko
func equal<T>(l1 : List<T>, l2 : List<T>, eq : (T, T) -> Bool) : Bool
```

Compare two lists for equality as specified by the given relation `eq` on the elements.

The function `isEq(l1, l2)` is equivalent to `lessThanEq(l1, l2) && lessThanEq(l2, l1)`, but the former is more efficient.

## tabulate

``` motoko
func tabulate<T>(n : Nat, f : Nat -> T) : List<T>
```

Generate a list based on a length and a function that maps from a list index to a list element.

## make

``` motoko
func make<X>(x : X) : List<X>
```

Create a list with exactly one element.

## replicate

``` motoko
func replicate<X>(n : Nat, x : X) : List<X>
```

Create a list of the given length with the same value in each position.

## zip

``` motoko
func zip<X, Y>(xs : List<X>, ys : List<Y>) : List<(X, Y)>
```

Create a list of pairs from a pair of lists.

If the given lists have different lengths, then the created list will have a length equal to the length of the smaller list.

## zipWith

``` motoko
func zipWith<X, Y, Z>(xs : List<X>, ys : List<Y>, f : (X, Y) -> Z) : List<Z>
```

Create a list in which elements are calculated from the function `f` and include elements occuring at the same position in the given lists.

If the given lists have different lengths, then the created list will have a length equal to the length of the smaller list.

## split

``` motoko
func split<X>(n : Nat, xs : List<X>) : (List<X>, List<X>)
```

Split the given list at the given zero-based index.

## chunks

``` motoko
func chunks<X>(n : Nat, xs : List<X>) : List<List<X>>
```

Split the given list into chunks of length `n`. The last chunk will be shorter if the length of the given list does not divide by `n` evenly.

## fromArray

``` motoko
func fromArray<A>(xs : [A]) : List<A>
```

Convert an array into a list.

## fromVarArray

``` motoko
func fromVarArray<A>(xs : [var A]) : List<A>
```

Convert a mutable array into a list.

## toArray

``` motoko
func toArray<A>(xs : List<A>) : [A]
```

Create an array from a list.

## toVarArray

``` motoko
func toVarArray<A>(xs : List<A>) : [var A]
```

Create a mutable array from a list.
