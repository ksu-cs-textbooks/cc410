---
type: "reveal"
hidden: true
---
<section>
    <h3>JUnit Tests</h3>
    <pre class="stretch"><code>import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;<br>
public class SquareTest{<br>
    &commat;Test
    public void testSquareConstructorShouldSetLength(){
        Square square = new Square(2.0);
        assertEquals(2.0, square.getLength());
    }
}</code></pre>
</section>
<section>
    <h3>Install Parameters Library</h3>
    <pre class="stretch java"><code style="font-size: 37px">dependencies {
    // Use JUnit Jupiter API for testing.
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.6.2', 
        'org.hamcrest:hamcrest:2.2', 
        'org.junit.jupiter:junit-jupiter-params'<br>
    // Use JUnit Jupiter Engine for testing.
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine'<br>
    // This dependency is used by the application.
    implementation 'com.google.guava:guava:29.0-jre'
}</code></pre>
</section>
<section>
    <h3>JUnit Parameterized Tests</h3>
    <pre class="stretch"><code style="font-size: 38px">import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.ValueSource;<br>
public class StoveTest{<br>
    @ParameterizedTest
    @ValueSource(doubles = {1.0, 2.1, 3.2, 4.3, 5.9})
    public void SetSquareLengthToPositiveValue(double setting){
        Square square = new Square(setting);
        assertEquals(setting, square.getLength());
    }
}</code></pre>
</section>
<section>
    <h3>JUnit Assertions</h3>
    <ul>
        <li>assertTrue | assertFalse</li>
        <li>assertEquals | assertNotEquals</li>
        <li>assertArrayEquals</li>
        <li>assertLinesMatch</li>
        <li>assertNull | assertNotNull</li>
        <li>assertSame | assertNotSame</li>
    </ul>
</section>
<section>
    <h3>Catching Exceptions</h3>
    <pre class="stretch java"><code>@Test
void exceptionTesting() {
    Exception exception = assertThrows(
        IllegalArgumentException.class, 
        () -> new Square(-1.0));
    assertEquals("Length cannot be negative", 
        exception.getMessage());
}</code></pre>
</section>
<section>
    <h3>Checking Output</h3>
    <pre class="stretch java"><code style="font-size: 38px">@Test 
public void testHelloWorldMain() {
    HelloWorld hw = new HelloWorld();<br>
    final PrintStream systemOut = System.out;
    ByteArrayOutputStream testOut = new ByteArrayOutputStream();
    System.setOut(new PrintStream(testOut));<br>
    hw.main(new String[]{});<br>
    System.setOut(systemOut);<br>
    assertEquals(testOut.toString(), "Hello World\n");
}</code></pre>
</section>
