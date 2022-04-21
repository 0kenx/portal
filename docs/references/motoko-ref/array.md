# Array

Functions on Arrays

## equal

``` motoko
func equal<A>(a : [A], b : [A], eq : (A, A) -> Bool) : Bool
```

Test if two arrays contain equal values

## append

``` motoko
func append<A>(xs : [A], ys : [A]) : [A]
```

Append the values of two input arrays @deprecated Array.append has critical performance flaws; use a Buffer, and Buffer.append, instead.

## sort

``` motoko
func sort<A>(xs : [A], cmp : (A, A) -> Order.Order) : [A]
```

Sorts the given array according to the `cmp` function. This is a *stable* sort.

``` motoko
import Array "mo:base/Array";
import Nat "mo:base/Nat";
let xs = [4, 2, 6];
assert(Array.sort(xs, Nat.compare) == [2, 4, 6])
```

## sortInPlace

``` motoko
func sortInPlace<A>(xs : [var A], cmp : (A, A) -> Order.Order)
```

Sorts the given array in place according to the `cmp` function. This is a *stable* sort.

``` motoko
import Array "mo:base/Array";
import Nat "mo:base/Nat";
let xs : [var Nat] = [var 4, 2, 6, 1, 5];
Array.sortInPlace(xs, Nat.compare);
assert(Array.freeze(xs) == [1, 2, 4, 5, 6])
```

## chain

``` motoko
func chain<A, B>(xs : [A], f : A -> [B]) : [B]
```

Transform each array value into zero or more output values, appended in order

## filter

``` motoko
func filter<A>(xs : [A], f : A -> Bool) : [A]
```

Output array contains each array-value if and only if the predicate is true; ordering retained.

## mapFilter

``` motoko
func mapFilter<A, B>(xs : [A], f : A -> ?B) : [B]
```

Output array contains each transformed optional value; ordering retained.

## foldLeft

``` motoko
func foldLeft<A, B>(xs : [A], initial : B, f : (B, A) -> B) : B
```

Aggregate and transform values into a single output value, by increasing indices.

## foldRight

``` motoko
func foldRight<A, B>(xs : [A], initial : B, f : (A, B) -> B) : B
```

Aggregate and transform values into a single output value, by decreasing indices.

## find

``` motoko
func find<A>(xs : [A], f : A -> Bool) : ?A
```

Returns optional first value for which predicate is true

## freeze

``` motoko
func freeze<A>(xs : [var A]) : [A]
```

Transform mutable array into immutable array

## flatten

``` motoko
func flatten<A>(xs : [[A]]) : [A]
```

Transform an array of arrays into a single array, with retained array-value order.

## map

``` motoko
func map<A, B>(xs : [A], f : A -> B) : [B]
```

Transform each value using a function, with retained array-value order.

## mapEntries

``` motoko
func mapEntries<A, B>(xs : [A], f : (A, Nat) -> B) : [B]
```

Transform each entry (index-value pair) using a function.

## mapResult

``` motoko
func mapResult<A, R, E>(xs : [A], f : A -> Result.Result<R, E>) : Result.Result<[R], E>
```

Maps a Result-returning function over an Array and returns either the first error or an array of successful values.

``` motoko
import Array "mo:base/Array";
import Result "mo:base/Result";
import Int "mo:base/Int";
func makeNatural(x : Int) : Result.Result<Nat, Text> =
  if (x >= 0) {
    #ok(Int.abs(x))
  } else {
    #err(Int.toText(x) # " is not a natural number.")
  };

assert(Array.mapResult<Int, Nat, Text>([0, 1, 2], makeNatural) == #ok([0, 1, 2]));
assert(Array.mapResult([-1, 0, 1], makeNatural) == #err("-1 is not a natural number."));
```

## make

``` motoko
func make<A>(x : A) : [A]
```

Make an array from a single value.

## vals

``` motoko
func vals<A>(xs : [A]) : I.Iter<A>
```

Returns `xs.vals()`.

## keys

``` motoko
func keys<A>(xs : [A]) : I.Iter<Nat>
```

Returns `xs.keys()`.

## thaw

``` motoko
func thaw<A>(xs : [A]) : [var A]
```

Transform an immutable array into a mutable array.

## init

``` motoko
func init<A>(size : Nat, initVal : A) : [var A]
```

Initialize a mutable array with `size` copies of the initial value.

## tabulate

``` motoko
func tabulate<A>(size : Nat, gen : Nat -> A) : [A]
```

Initialize an immutable array of the given size, and use the `gen` function to produce the initial value for every index.

## tabulateVar

``` motoko
func tabulateVar<A>(size : Nat, gen : Nat -> A) : [var A]
```

Initialize a mutable array using a generation function
