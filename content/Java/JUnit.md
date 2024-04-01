## JUnit4 - Basic annotations

### Following are the most commonly used annotations and their usage in a basic unit test written in JUnit 4.

- `@Test` - Marks the method as a test method.
- `@Before` and `@After` sandwiches **each test method** in the class.
- `@BeforeClass` and `@AfterClass` sandwiches **all of the test methods** in a JUnit test class.
### Following is the execution order of the above mentioned methods when a JUnit4 test is run.

1. Method annotated with `@BeforeClass`
2. Method annotated with `@Before`
3. First method annotated with `@Test` i.e. `test1()`.
4. Method annotated with `@After`
5. Method annotated with `@Before`
6. Second method annotated with `@Test` i.e. `test2()`.
7. Method annotated with `@After`
8. Method annotated with `@AfterClass`
## `@BeforeClass`

Method annotated with `@BeforeClass` will execute once before any of the test methods in this class.

This method could be used to set up any test fixtures that are computationally expensive and shared by several test methods. e.g. establishing database connections 

Sometimes several tests need to share computationally expensive setup (like logging into a database). While this can compromise the independence of tests, sometimes it is a necessary optimization. 
## `@AfterClass`

Method annotated with `@AfterClass` will execute once after all of the test methods are executed in this class.
If you allocate expensive external resources in a `@BeforeClass` method you need to release them after all the tests in the class have run. Annotating a public static void method with `@AfterClass` causes that method to be run after all the tests in the class have been run. All `@AfterClass` methods are guaranteed to run even if a `BeforeClass` method throws an exception.




---
## LINKS
[JUnit tutorial](https://javacodehouse.com/blog/junit-tutorial/)

