---
title: Profiles
type: guide
order: 6
---

Infection supports the use of mutator profiles for the command line and configuration file.

The following configuration file will use the `@default` profile, but turn off the `@function_signature` profile. 
On top of that, it does not apply the `TrueValue` mutator on any classes that match the provided ignore patterns. In particular, `TrueValue` mutator does not mutate the code inside `Full\NameSpaced\Class` class and inside `create()` method of all `SourceClass` classes.

These ignores can also be added to profiles, to ensure infection is as flexible as you need it. 

All profiles are prepended by an `@` and in snake case, while all mutators are in PascalCase. 

``` json
{
    "source": {
        "directories": [
            "src"
        ]
    },
    "timeout": 10,
    "logs": {
        "text": "infection-log.txt"
    },
    "mutators": {
        "@default": true,
        "@function_signature": false,
        "TrueValue": {
            "ignore": [
                "NameSpace\\*\\SourceClass::method",
                "Full\\NameSpaced\\Class"
            ]
        }
    }
}
```

## The Profiles

Currently, infection supports the following profiles:

### `@arithmetic`

Containes the following mutators:

* [Assignment](/guide/mutators.html#Binary-Arithmetic)
* [AssignmentEqual](/guide/mutators.html#Binary-Arithmetic)
* [BitwiseAnd](/guide/mutators.html#Binary-Arithmetic)
* [BitwiseNot](/guide/mutators.html#Binary-Arithmetic)
* [BitwiseOr](/guide/mutators.html#Binary-Arithmetic)
* [BitwiseXor](/guide/mutators.html#Binary-Arithmetic)
* [Decrement](/guide/mutators.html#Increments)
* [DivEqual](/guide/mutators.html#Binary-Arithmetic)
* [Division](/guide/mutators.html#Binary-Arithmetic)
* [Exponentiation](/guide/mutators.html#Binary-Arithmetic)
* [Increment](/guide/mutators.html#Increments)
* [Minus](/guide/mutators.html#Binary-Arithmetic)
* [MinusEqual](/guide/mutators.html#Binary-Arithmetic)
* [ModEqual](/guide/mutators.html#Binary-Arithmetic)
* [Modulus](/guide/mutators.html#Binary-Arithmetic)
* [MulEqual](/guide/mutators.html#Binary-Arithmetic)
* [Multiplication](/guide/mutators.html#Binary-Arithmetic)
* [Plus](/guide/mutators.html#Binary-Arithmetic)
* [PlusEqual](/guide/mutators.html#Binary-Arithmetic)
* [PowEqual](/guide/mutators.html#Binary-Arithmetic)
* [ShiftLeft](/guide/mutators.html#Binary-Arithmetic)
* [ShiftRight](/guide/mutators.html#Binary-Arithmetic)

### `@boolean`

Containes the following mutators:

* [ArrayItem](/guide/mutators.html#Boolean-Substitution)
* [FalseValue](/guide/mutators.html#Boolean-Substitution)
* [IdenticalEqual](/guide/mutators.html#Boolean-Substitution)
* [LogicalAnd](/guide/mutators.html#Boolean-Substitution)
* [LogicalLowerAnd](/guide/mutators.html#Boolean-Substitution)
* [LogicalLowerOr](/guide/mutators.html#Boolean-Substitution)
* [LogicalNot](/guide/mutators.html#Boolean-Substitution)
* [LogicalOr](/guide/mutators.html#Boolean-Substitution)
* [NotIdenticalNotEqual](/guide/mutators.html#Boolean-Substitution)
* [TrueValue](/guide/mutators.html#Boolean-Substitution)
* [Yield_](/guide/mutators.html#Boolean-Substitution)

### `@cast`

Containes the following mutators:

* [CastArray](/guide/mutators.html#Type-Casting)
* [CastBool](/guide/mutators.html#Type-Casting)
* [CastFloat](/guide/mutators.html#Type-Casting)
* [CastInt](/guide/mutators.html#Type-Casting)
* [CastObject](/guide/mutators.html#Type-Casting)
* [CastString](/guide/mutators.html#Type-Casting)

### `@conditional_boundary`

Containes the following mutators:

* [GreaterThan](/guide/mutators.html#Conditional-Boundaries)
* [GreaterThanOrEqualTo](/guide/mutators.html#Conditional-Boundaries)
* [LessThan](/guide/mutators.html#Conditional-Boundaries)
* [LessThanOrEqualTo](/guide/mutators.html#Conditional-Boundaries)

### `@conditional_negotiation`

Containes the following mutators:

* [Equal](/guide/mutators.html#Negated-Conditionals)
* [GreaterThanNegotiation](/guide/mutators.html#Negated-Conditionals)
* [GreaterThanOrEqualToNegotiation](/guide/mutators.html#Negated-Conditionals)
* [Identical](/guide/mutators.html#Negated-Conditionals)
* [LessThanNegotiation](/guide/mutators.html#Negated-Conditionals)
* [LessThanOrEqualToNegotiation](/guide/mutators.html#Negated-Conditionals)
* [NotEqual](/guide/mutators.html#Negated-Conditionals)
* [NotIdentical](/guide/mutators.html#Negated-Conditionals)

### `@function_signature`

Containes the following mutators:

* [PublicVisibility](/guide/mutators.html#Function-Signature)
* [ProtectedVisibility](/guide/mutators.html#Function-Signature)

### `@number`

Containes the following mutators:

* [DecrementInteger](/guide/mutators.html#Literal-Numbers)
* [IncrementInteger](/guide/mutators.html#Literal-Numbers)
* [OneZeroInteger](/guide/mutators.html#Literal-Numbers)
* [OneZeroFloat](/guide/mutators.html#Literal-Numbers)

### `@operator`

Containes the following mutators:

* [Break_](/guide/mutators.html#Loop)
* [Continue_](/guide/mutators.html#Loop)
* [Throw_](/guide/mutators.html#Exceptions)

### `@regex`

Containes the following mutators:

* [PregQuote](/guide/mutators.html#Regex)
* [PregMatchMatches](/guide/mutators.html#Regex)

### `@removal`

Containes the following mutators:

* [FunctionCallRemoval](/guide/mutators.html#Removal)
* [MethodCallRemoval](/guide/mutators.html#Removal)

### `@return_value`

Containes the following mutators:

* [FloatNegation](/guide/mutators.html#Return-Values)
* [FunctionCall](/guide/mutators.html#Return-Values)
* [IntegerNegation](/guide/mutators.html#Return-Values)
* [NewObject](/guide/mutators.html#Return-Values)
* [This](/guide/mutators.html#Return-Values)

### `@sort`

Containes the following mutators:

* [Spaceship](/guide/mutators.html#Sorting)

### `@zero_iteration`

Containes the following mutators:

* [Foreach_](/guide/mutators.html#Loop)
* [For_](/guide/mutators.html#Loop)

### `@default`

This is the default profile, which currently contains **all** mutators, and is used if no mutator or profile is chosen.

>Feel free to request a new profile to be added in Github's issues.
