---
type: "reveal"
hidden: true
---
<section>
	<h2>CC 410 - Week 3</h2>
</section>
<section>
	<h3>Wrapping Up</h3>
	<ul>
		<li>2/7 - Final Project 1</li>
		<li>2/7 - Module 2: OOP</li>
		<li>2/7 - OOP Example</li>
		<li>2/7 - Restaurant 1</li>
	</ul>
</section>
<section>
	<h3>This Week</h3>
	<ul>
		<li>2/14 - Documentation, Testing, UML</li>
		<li>2/14 - Doc & Testing Example</li>
		<li>2/14 - Restaurant 2</li>
	</ul>
</section>
<section>
	<h3>Updates</h3>
	<ul>
		<li>Discord Channel<br>https://discordbot.cs.ksu.edu</li>
		<li>Grading - Rubric on Canvas<br>Code Comments on GitHub</li>
		<li>So far, so good?</li>
	</ul>
</section>
<section>
	<h3>Milestone 2</h3>
	<ul>
		<li>Unit Tests (~423)</li>
		<li>Documentation Comments</li>
		<li>UML Class Diagram</li>
		<li>3-8 hours</li>
		<li>~3500-4000 LOC</li>
		<li>Feedback welcome!</li>
	</ul>
</section>
<section>
	<h3>Milestone 2 Hints</h3>
	<ul>
		<li>Do Not Look at Source!</li>
		<li>Use Global Attributes</li>
		<li>Generalize (but not ingredients)</li>
		<li>Look at Enum Parameterized Tests</li>
	</ul>
</section>
<section>
    <h3>Generalized Tests</h3>
    <div style="float: right; width: 50%">
        <h6>Python</h6>
        <pre class="python stretch" style="font-size: 20px"><code>class TestTheRiker:<br>
	PRICE: float = 17.01
	CALORIES: int = 1701<br>
	def test_has_correct_price(self) -> None:
		"""The price is correct."""
		item: TheRiker = TheRiker()
		assert_that(item.price,
		            is_(TestTheRiker.PRICE))<br>
	def test_has_correct_calories(self) -> None:
		"""The calories is correct."""
		item: TheRiker = TheRiker()
		assert_that(item.calories,
		            is_(TestTheRiker.CALORIES))</code></pre>
    </div>
    <div style="float: left; width: 50%">
        <h6>Java</h6>
		<pre class="java stretch" style="font-size: 20px"><code>public class TheRikerTest {<br>
    private static final double PRICE = 17.01;
    private static final int CALORIES = 1701;<br>
    /**
     * The price is correct.
     */
    @Test
    public void testHasCorrectPrice() {
        TheRiker item = new TheRiker();
        assertThat(item.getPrice(), is(PRICE));
    }<br>
    /**
     * The calories is correct.
     */
    @Test
    public void testHasCorrectCalories() {
        TheRiker item = new TheRiker();
        assertThat(item.getCalories(), is(CALORIES));
    }
}</code></pre>
    </div>
</section>
<section>
	<h3>Looking Ahead</h3>
	<ul>
		<li>Module 4 - Inheritance</li>
		<li>Module 5 - Debugging<br>Final Project 2</li>
		<li>Module 6 - GUI Basics</li>
		<li>Module 7 - Event-Driven Programming</li>
		<li>GUIs, Web APIs, etc.</li>
	</ul>
</section>
<section>
	<img class="plain stretch" src="https://media.giphy.com/media/gw3IWyGkC0rsazTi/giphy.gif">
	<p class="imagecredit">Image Credit: <a href="https://giphy.com/gifs/test-gw3IWyGkC0rsazTi/">Giphy</a></p>
</section>