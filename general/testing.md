# Testing

Tests are the way to verify code, and make sure it works as expected.

There are many kinds of tests, and many ways to handle them, which will depend on the language and frameworks being used.

The two most common kinds of test are unit and integration tests. But there are many others, such as smoke tests or regression tests. Sometimes the difference between one kind to another is sutile, and each person will have their own ideas about them. But in general these would be the ones we want to remember:

| Type of test | Verifies... |
| :--- | :--- |
| Acceptance | ..that the code does what it was designed to |
| Black box | ...a piece of code where the exact workings of the internal logic is unknown |
| Integration | ...the combined logic of several components |
| Regression | ...that the code still is working |
| Smoke | ...that the code does not burst into flames when run |
| Stress | ...that the code can keep working under severe stress |
| Unit | ...the smallest possible piece of logic |
| White box | ...a piece of code where the internal logic can be probed |

## Methodologies

* Test Driven Development

## When to use tests

Run with each code change to validate the code base and the changes. Let the Continuous Integration process handle this. Add tests to cover all use cases, and to make sure a bug doesn't reappear once solved.

## In which way are tests useful?

Test won't make a program bug free, but they remove to need to start the application to test it manually. Also the test will never forget which cases should be tested, and under which conditions.

If all the tests are correctly planned the will validate the application, ensuring it fits into the specification.

## Integration

Some test may require a complex environment, where several services are integrated. For these cases there are some small guidelines:

* Use embedded databases
* Mock or stub external services

