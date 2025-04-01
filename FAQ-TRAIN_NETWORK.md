# Train Network Assignment FAQ

- [Train Network Assignment FAQ](#train-network-assignment-faq)
  - [Should I fill `queries.pl`?](#should-i-fill-queriespl)
  - [Can I use built-in predicate `P/n`?](#can-i-use-built-in-predicate-pn)
  - [How can I compute \& carry "so-far" results?](#how-can-i-compute--carry-so-far-results)
  - [Should the output/results of queries be listed in the order as in the spec?](#should-the-outputresults-of-queries-be-listed-in-the-order-as-in-the-spec)
  - [Could a link exist on a non-defined city?](#could-a-link-exist-on-a-non-defined-city)
  - [How precise the time needs to be? My solution yields  5.416666666666666 rather than 5.416666666666667!](#how-precise-the-time-needs-to-be-my-solution-yields--5416666666666666-rather-than-5416666666666667)
  - [Where are the test cases for the assignment?](#where-are-the-test-cases-for-the-assignment)

## Should I fill `queries.pl`?

No. Some answers were wrongly provided, so we will disregard the queries and only focus on the modeling of the Ontario network 😉

## Can I use built-in predicate `P/n`?

This project assignment can be solved neatly using plain basic Prolog built-in predicates. As the Language Restriction section in the specs states you are not to use advanced predicates or libraries. These include all-solution predicates like `findall/3` for example or the constraint libraries: none are needed anyways.

If in doubt always ask in the forum. Some other predicates that you shall not use are:

- `table/1`, `order_by/1`, `sort/2`, `msort/2`

Some predicates that you can use as they are still basic are:

- `nth0/3`, `nth1/3`, `reverse/2`, `min/2`, `max/2`, `last/2`.
- All the type checking predicates: https://www.swi-prolog.org/pldoc/man?section=typetest

## How can I compute & carry "so-far" results?

A usual strategy for computing something is to carry intermediate results until the end, and once there, just equate the final result with the result so far.

For example, this is how I can sum a list of numbers:

```prolog
sumar(L, R) :- sumar(L, 0, R).

sumar([], SumSoFar, SumSoFar).
sumar([X|L], SumSoFar, Result) :-
    SumSoFar2 is  SumSoFar + X,
    sumar(L, SumSoFar2, Result).
```

Check a run:

```prolog
?- sumar([1,2,3,4], R).
R = 10.
```

## Should the output/results of queries be listed in the order as in the spec?

No! When we have answers from Prolog, we really do not care their order, they are logically true answers. Order doesn't matter.

## Could a link exist on a non-defined city?

No! Every city mentioned in a link will have its corresponding city definition.

## How precise the time needs to be? My solution yields  5.416666666666666 rather than 5.416666666666667!

No problem. We will round to three the most three significant digits, so all good with that answer, they are equivalent!

## Where are the test cases for the assignment?

As in any software development, _you_ are to are meant to develop your test cases from requirements; it is part of the process. The workshops exercises, which bring some test cases, are of different nature and play a different role in your course, more formative assessment.
