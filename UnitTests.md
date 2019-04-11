# 1. Kinds of 'fakes'

1.1. Dummy object
* An additional parameter
* The test and the code under test shouldn't care for there
* Example: config name

1.2. Stub
* Replace external dependency
* Control indirect input
* Example: when(mock.methodcall()).thenReturn(...)

1.3. Spy
* Extension of stub 
* Record how they were called for latter verification
* Verification happens manually.

1.4. Mock
* They should meet expectations(?) -> I'm not sure. There is no big diffrence in unit tests vs Spy.

1.5. Fake object
* Example: creating new class manually to replace dependency.

# 2. TestNG vs Mockito
Junit creates new class for each test. TestNG doesn't.
TestNg has better Parametrized tests, in Junit we need another dependency.
 
# 3. Test names
Suggestion: testSomeThingShouldDoSomethingWhenSomething
Better: testSomeThing_ShouldDoSomething_WhenSomething (for long names)

# 4. Avoid using static util classes.
* Can't be mocked
# 5. Make external dependencies replecable -> We want test only unit of code.  

# 6. Test orginally exposed meethod only
* Helps to detect design problem with class (eg. private methods uses dependencies that cant be mocked)
* Private methods should be tested via public methods.

# 7. Visible for testing only
* Guava @VisibleForTesting is perfect for it
* If Guava is not available, we can create own annotation.

# 8. Assertions
* Do not use assertEquals everywhere.
* Prefer assrtion on state over verification of behavior -> easier to change test after refactor
* Example: converter and a service as a dependency: The converter call is not business critical, but service call probably is.
# 9. Don't mock model classes
* Since they don't contain logic, they should not be mocked.
* You can create it manually.
* Reduces dependency on framework.

# 10. Mocking
* Do not mock everything:
when(a.call(String.class))
better: when(a.call("actual value))
Because test is easier to understand 

# 11. Testing abstract classes
* One solution: test all subclasses and duplicate code in the tests.
* Create abstract test class and extend it for every 'production' subclass.
