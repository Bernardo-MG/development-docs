# Testing

Tests are the way to ensure the code behaves as expected. There are many ways to handle testing during development, but first we need to find out which types of test exist, and which ones we want to use.

The two most common kinds of test, the ones everybody talks about, are unit and integration tests. But there are others (which in some cases may be also included among unit and integration tests) such as smoke tests or regression tests. Sometimes the difference between one kind to another is sutile, and each person will have their own ideas about them. But in general these would be the ones we want to remember:

Type of test|Verifies...
---|---
Acceptance|..that the code does what it was designed to
Black box|...a piece of code where the exact workings of the internal logic is unknown
Integration|...the combined logic of several components
Regression|...that the code still is working
Smoke|...that the code does not burst into flames when run
Stress|...that the code can keep working under severe stress
Unit|...the smallest possible piece of logic
White box|...a piece of code where the internal logic can be probed

## When to use tests

Tests are to be run with each code change to validate them. The CI process should take care of this, to ensure the code base is always in a valid state, or that any potential error is identified.

## In which way are tests useful?

Test do not make a program bug free, but they remove to need to start and manually test the application after each modification.

Another important notion is that they validate the application, ensure it fits into the specification.
