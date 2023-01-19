---
title: "Arrange, Act, Assert"
weight: 15
pre: "3. "
---

Most of our unit tests have been following a particular pattern, commonly called **arrange, act, assert.** Let's quickly review that pattern, as it is very important to understand how it integrates with the use of test doubles later in this chapter.

A simple unit test following the arrange, act, assert pattern consists of three major steps:

1. **Arrange** - first, the objects to be tested and any supporting data is created within the test.
2. **Act** - secondly, the operation being tested is carried out, usually by calling one or more methods.
3. **Assert** - once the operation is complete, we use assertions to verify that the outcome of the operation is correct.

In some instances, we may also include a fourth step, **Teardown**, which is used to reset the state back to its initial state, if needed. There are times when our arrange step makes some changes to the environment that must be reversed before we can continue. 

Let's go back to a unit test you may have explored in example 3 and see how it fits the arrange, act, assert pattern.

{{< tabs >}}

{{% tab name="Java" %}}

```java
@Test
public void testSevenWrongGuessesShouldLose() {
    // Arrange
    GuessingGame game = new GuessingGame("secret");
    
    // Act
    game.guess('a');
    game.guess('b');
    game.guess('d');
    game.guess('f');
    game.guess('g');
    game.guess('h');
    game.guess('i');
    
    // Assert
    assertTrue(game.isLost());
}
```

{{% /tab %}}

{{% tab name="Python" %}}

```python
def test_seven_wrong_guesses_should_lose(self):
    # Arrange
    game = GuessingGame("secret")
    
    # Act
    game.guess('a')
    game.guess('b')
    game.guess('d')
    game.guess('f')
    game.guess('g')
    game.guess('h')
    game.guess('i')
    
    # Assert
    assert game.lost
```

{{% /tab %}}

{{< /tabs >}}

In both of these tests, we start in the **arrange** portion by instantiating a `GuessingGame` object, which is the object we will be testing. Then, in the **act** phase, we call several methods in the `GuessingGame` object - in this case, we are checking that seven incorrect guesses should cause the game to be lost, so we must make seven incorrect guesses. Finally, in the **assert** section, we use a simple assertion to make sure the game has been lost. 

{{% notice note "Behavior-Driven Development" %}}

One common alternative to this approach comes from [**behavior-driven development**](https://en.wikipedia.org/wiki/Behavior-driven_development). In this development process, which is effectively an extension of the [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development) process we've learned about, software specifications are written to match the behaviors that a user might expect to see when the application is running. Such a specification typically follows a [**given, when, then**](https://en.wikipedia.org/wiki/Given-When-Then) structure. Here's a short example of a specification from [Wikipedia](https://en.wikipedia.org/wiki/Behavior-driven_development).

```tex
Given a 5 by 5 game
When I toggle the cell at (3, 2)
Then the grid should look like
.....
.....
.....
..X..
.....
```

The beauty of such a specification is that it can be easily read by a non-technical user, and allows quick and easy discussion with end users and clients regarding how the software should actually function. Once the specification is developed, we can then write unit tests that will use the specification and verify that the program operates as intended. Here's an example from [Wikipedia](https://en.wikipedia.org/wiki/Behavior-driven_development) in Java using the [JBehave](https://jbehave.org/) framework.

```java
private Game game;
private StringRenderer renderer;

@Given("a $width by $height game")
public void theGameIsRunning(int width, int height) {
    game = new Game(width, height);
    renderer = new StringRenderer();
    game.setObserver(renderer);
}
    
@When("I toggle the cell at ($column, $row)")
public void iToggleTheCellAt(int column, int row) {
    game.toggleCellAt(column, row);
}

@Then("the grid should look like $grid")
public void theGridShouldLookLike(String grid) {
    assertThat(renderer.asString(), equalTo(grid));
}
```

This testing strategy requires a bit more work than the unit testing we've covered in this course, but it can be very powerful when put into use.

{{% / notice %}}
