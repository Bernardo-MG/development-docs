# Testing

Tests are the way to ensure the code behaves as expected and wished. There are many ways to handle testing during development, but first we need to find out which types of test exist, and which ones we want to use.

The two most common kinds of test, the ones everybody talks about, are unit and integration tests. But there are other kinds, which may or not be also unit and integration tests, such as smoke tests or regression tests. Sometimes the difference between one kind to another is not too clear, and each person will have their own description, and opinions, about them. But in general terms these would be the ones we want to remember:

Type of test|Verifies...
---|---
Acceptance|..that the code does as it was requested
Black box|...a piece of code where the exact workings of the internal logic is unknown
Integration|...the combined logic of several components
Regression|...the code still is working
Smoke|...the code does not burst into flames when run
Stress|...the code can keep working under severe stress
Unit|...the smallest possible piece of logic
White box|...a piece of code where the internal logic can be probed