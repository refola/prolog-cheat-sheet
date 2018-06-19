# Prolog cheatsheet
A concise listing of prolog syntax and built-in predicates related to my studies, organized by which tutorial I first learned them in.

# Prolog Koans

Source: [https://github.com/araneforseti/prolog-koans](https://github.com/araneforseti/prolog-koans)

## Basic predicate syntax: `p(X) :- q(X), r(X)`

	% This comment should explain why we need our primes to be beyond lagomorph comprehension.
	rabbitVulnerablePrime(2).
	rabbitVulnerablePrime(3).
	rabbitVulnerablePrime(5). % Do they really understand 5? We better keep this just to be safe.
	% rabbitVulnerablePrime(X) is false for anything else, so we better have captured every true case and only the true cases.

	alwaysTrue(Vars).

	compoundPredicate(X, Y) :-
		pred1(X),
		pred2(X, Y).

## Equality-like comparisons (`=`, etc)

	X is Y  % X is the value that results from simplifying the Y as an arithmetic expression. Attempts unification of variable X to the value of Y.
	X =:= Y % X and Y evaluate to the same arithmetic value. No unification.
	X #= Y  % X and Y are equal as arithmetic integer expressions. Attempts bidirectional unification of all variables in each expression. (load with use_module(library(clpfd)).)
	X = Y   % Can X and Y be unified into the same value? If so, unify them.
    X \= Y  % Would unifying X and Y fail?
	X == Y  % Are X and Y already the same value?
    X \== Y % Are X and Y different?

## Lists (`[]`)

	checkFirstAndRest([First|Rest) :-
		check(First),
		check(Rest).

	isEmpty([]).

	singleton([X]).

	hasTwo([X, Y]).

	atLeastTwo([X, _]).

	% built-ins
	last(Xs, LastX).
	element(Index, Intergers, Value). % only works with integer lists and 1-indexed; see nth0 and nth1
	nth0(Index, Values, Value). % 0-indexed; see alse nth1
	length(Xs, Count).
	reverse(Xs, Reversed).
	append(Xs, Ys, XsThenYs).
	flatten(Nested, Flat). % remove all but outermost "[" and "]" from nested list

## Ignored and placeholder variables (`_`)

	checkOnlyOneVar(X, _) :-
		check(X).

	checkFirstOfList([First|_]) :-
		check(First).
