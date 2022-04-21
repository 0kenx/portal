# Option

Typesafe nulls

Optional values can be seen as a typesafe `null`. A value of type `?Int` can be constructed with either `null` or `?42`. The simplest way to get at the contents of an optional is to use pattern matching:

``` motoko
let optionalInt1 : ?Int = ?42;
let optionalInt2 : ?Int = null;

let int1orZero : Int = switch optionalInt1 {
  case null 0;
  case (?int) int;
};
assert int1orZero == 42;

let int2orZero : Int = switch optionalInt2 {
  case null 0;
  case (?int) int;
};
assert int2orZero == 0;
```

The functions in this module capture some common operations when working with optionals that can be more succinct than using pattern matching.

## get

``` motoko
func get<T>(x : ?T, default : T) : T
```

Unwraps an optional value, with a default value, i.e. `get(?x, d) = x` and `get(null, d) = d`.

## getMapped

``` motoko
func getMapped<A, B>(x : ?A, f : A -> B, default : B) : B
```

Unwraps an optional value using a function, or returns the default, i.e. `option(?x, f, d) = f x` and `option(null, f, d) = d`.

## map

``` motoko
func map<A, B>(x : ?A, f : A -> B) : ?B
```

Applies a function to the wrapped value. \`null’s are left untouched.

``` motoko
import Option "mo:base/Option";
assert Option.map<Nat, Nat>(?42, func x = x + 1) == ?43;
assert Option.map<Nat, Nat>(null, func x = x + 1) == null;
```

## iterate

``` motoko
func iterate<A>(x : ?A, f : A -> ())
```

Applies a function to the wrapped value, but discards the result. Use `iterate` if you’re only interested in the side effect `f` produces.

``` motoko
import Option "mo:base/Option";
var counter : Nat = 0;
Option.iterate(?5, func (x : Nat) { counter += x });
assert counter == 5;
Option.iterate(null, func (x : Nat) { counter += x });
assert counter == 5;
```

## apply

``` motoko
func apply<A, B>(x : ?A, f : ?(A -> B)) : ?B
```

Applies an optional function to an optional value. Returns `null` if at least one of the arguments is `null`.

## chain

``` motoko
func chain<A, B>(x : ?A, f : A -> ?B) : ?B
```

Applies a function to an optional value. Returns `null` if the argument is `null`, or the function returns `null`.

## flatten

``` motoko
func flatten<A>(x : ??A) : ?A
```

Given an optional optional value, removes one layer of optionality.

``` motoko
import Option "mo:base/Option";
assert Option.flatten(?(?(42))) == ?42;
assert Option.flatten(?(null)) == null;
assert Option.flatten(null) == null;
```

## make

``` motoko
func make<A>(x : A) : ?A
```

Creates an optional value from a definite value.

``` motoko
import Option "mo:base/Option";
assert Option.make(42) == ?42;
```

## isSome

``` motoko
func isSome(x : ?Any) : Bool
```

Returns true if the argument is not `null`, otherwise returns false.

## isNull

``` motoko
func isNull(x : ?Any) : Bool
```

Returns true if the argument is `null`, otherwise returns false.

## assertSome

``` motoko
func assertSome(x : ?Any)
```

Asserts that the value is not `null`; fails otherwise. @deprecated Option.assertSome will be removed soon; use an assert expression instead

## assertNull

``` motoko
func assertNull(x : ?Any)
```

Asserts that the value *is* `null`; fails otherwise. @deprecated Option.assertNull will be removed soon; use an assert expression instead

## unwrap

``` motoko
func unwrap<T>(x : ?T) : T
```

Unwraps an optional value, i.e. `unwrap(?x) = x`.

@deprecated Option.unwrap is unsafe and fails if the argument is null; it will be removed soon; use a `switch` or `do?` expression instead
