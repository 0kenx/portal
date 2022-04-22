# Nat8

8-bit unsigned integers with checked arithmetic

Most operations are available as built-in operators (e.g. `1 + 1`).

## Nat8

``` motoko
type Nat8 = Prim.Types.Nat8
```

8-bit natural numbers.

## toNat

``` motoko
let toNat : Nat8 -> Nat
```

Conversion.

## fromNat

``` motoko
let fromNat : Nat -> Nat8
```

Conversion. Traps on overflow/underflow.

## fromIntWrap

``` motoko
let fromIntWrap : Int -> Nat8
```

Conversion. Wraps on overflow/underflow.

## toText

``` motoko
func toText(x : Nat8) : Text
```

Returns the Text representation of `x`.

## min

``` motoko
func min(x : Nat8, y : Nat8) : Nat8
```

Returns the minimum of `x` and `y`.

## max

``` motoko
func max(x : Nat8, y : Nat8) : Nat8
```

Returns the maximum of `x` and `y`.

## equal

``` motoko
func equal(x : Nat8, y : Nat8) : Bool
```

Returns `x == y`.

## notEqual

``` motoko
func notEqual(x : Nat8, y : Nat8) : Bool
```

Returns `x != y`.

## less

``` motoko
func less(x : Nat8, y : Nat8) : Bool
```

Returns `x < y`.

## lessOrEqual

``` motoko
func lessOrEqual(x : Nat8, y : Nat8) : Bool
```

Returns `x ⇐ y`.

## greater

``` motoko
func greater(x : Nat8, y : Nat8) : Bool
```

Returns `x > y`.

## greaterOrEqual

``` motoko
func greaterOrEqual(x : Nat8, y : Nat8) : Bool
```

Returns `x >= y`.

## compare

``` motoko
func compare(x : Nat8, y : Nat8) : {#less; #equal; #greater}
```

Returns the order of `x` and `y`.

## add

``` motoko
func add(x : Nat8, y : Nat8) : Nat8
```

Returns the sum of `x` and `y`, `x + y`. Traps on overflow.

## sub

``` motoko
func sub(x : Nat8, y : Nat8) : Nat8
```

Returns the difference of `x` and `y`, `x - y`. Traps on underflow.

## mul

``` motoko
func mul(x : Nat8, y : Nat8) : Nat8
```

Returns the product of `x` and `y`, `x * y`. Traps on overflow.

## div

``` motoko
func div(x : Nat8, y : Nat8) : Nat8
```

Returns the division of `x by y`, `x / y`. Traps when `y` is zero.

## rem

``` motoko
func rem(x : Nat8, y : Nat8) : Nat8
```

Returns the remainder of `x` divided by `y`, `x % y`. Traps when `y` is zero.

## pow

``` motoko
func pow(x : Nat8, y : Nat8) : Nat8
```

Returns `x` to the power of `y`, `x ** y`. Traps on overflow.

## bitnot

``` motoko
func bitnot(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise negation of `x`, `^x`.

## bitand

``` motoko
func bitand(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise and of `x` and `y`, `x & y`.

## bitor

``` motoko
func bitor(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise or of `x` and `y`, `x \| y`.

## bitxor

``` motoko
func bitxor(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise exclusive or of `x` and `y`, `x ^ y`.

## bitshiftLeft

``` motoko
func bitshiftLeft(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise shift left of `x` by `y`, `x << y`.

## bitshiftRight

``` motoko
func bitshiftRight(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise shift right of `x` by `y`, `x >> y`.

## bitrotLeft

``` motoko
func bitrotLeft(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise rotate left of `x` by `y`, `x <<> y`.

## bitrotRight

``` motoko
func bitrotRight(x : Nat8, y : Nat8) : Nat8
```

Returns the bitwise rotate right of `x` by `y`, `x <>> y`.

## bittest

``` motoko
func bittest(x : Nat8, p : Nat) : Bool
```

Returns the value of bit `p mod 8` in `x`, `(x & 2^(p mod 8)) == 2^(p mod 8)`.

## bitset

``` motoko
func bitset(x : Nat8, p : Nat) : Nat8
```

Returns the value of setting bit `p mod 8` in `x` to `1`.

## bitclear

``` motoko
func bitclear(x : Nat8, p : Nat) : Nat8
```

Returns the value of clearing bit `p mod 8` in `x` to `0`.

## bitflip

``` motoko
func bitflip(x : Nat8, p : Nat) : Nat8
```

Returns the value of flipping bit `p mod 8` in `x`.

## bitcountNonZero

``` motoko
let bitcountNonZero : (x : Nat8) -> Nat8
```

Returns the count of non-zero bits in `x`.

## bitcountLeadingZero

``` motoko
let bitcountLeadingZero : (x : Nat8) -> Nat8
```

Returns the count of leading zero bits in `x`.

## bitcountTrailingZero

``` motoko
let bitcountTrailingZero : (x : Nat8) -> Nat8
```

Returns the count of trailing zero bits in `x`.

## addWrap

``` motoko
func addWrap(x : Nat8, y : Nat8) : Nat8
```

Returns the sum of `x` and `y`, `x +% y`. Wraps on overflow.

## subWrap

``` motoko
func subWrap(x : Nat8, y : Nat8) : Nat8
```

Returns the difference of `x` and `y`, `x -% y`. Wraps on underflow.

## mulWrap

``` motoko
func mulWrap(x : Nat8, y : Nat8) : Nat8
```

Returns the product of `x` and `y`, `x *% y`. Wraps on overflow.

## powWrap

``` motoko
func powWrap(x : Nat8, y : Nat8) : Nat8
```

Returns `x` to the power of `y`, `x **% y`. Wraps on overflow.
