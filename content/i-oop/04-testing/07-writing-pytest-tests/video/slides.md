---
type: "reveal"
hidden: true
---
<section>
    <h3>pytest Tests</h3>
    <pre class="stretch"><code>from src.shapes.Square import Square<br>
class TestSquare:<br>    
    def test_square_constructor_should_set_length(self):
        square = Square(2.0)
        assert square.length == 2.0</code></pre>
</section>
<section>
    <h3>pytest Parameterized Tests</h3>
    <pre class="stretch"><code style="font-size: 38px">from src.shapes.Square import Square
import pytest<br>
class TestSquare:<br> 
    @pytest.mark.parametrize("value", [1.0, 2.1, 3.2, 4.3, 5.9])
    def test_set_length_to_positive_value(self, value):
        square = Square(value)
        assert square.length == value</code></pre></code></pre>
</section>
<section>
    <h3>pytest Assertions</h3>
    <ul>
        <li>assert &lt;boolean expression></li>
        <li>assert actual == pytest.approx(expected)</li>
        <li>assert actual is expected</li>
        <li>assert actual is None</li>
    </ul>
</section>
<section>
    <h3>Catching Exceptions</h3>
    <pre class="python"><code>def test_zero_division():
    with pytest.raises(ZeroDivisionError):
        calculator.divide(1, 0)</code></pre>
</section>
<section>
    <h3>Checking Output</h3>
    <pre class="stretch python"><code style="font-size: 38px">from pytest import CaptureFixture
from _pytest.capture import CaptureResult
from typing import Any
from src.hello.HelloWorld import HelloWorld<br>
def test_hello_world(self, capsys: CaptureFixture[Any]) -> None:
    HelloWorld.main(["HelloWorld"])
    captured: CaptureResult[Any] = capsys.readouterr()
    assert captured.out == "Hello World\n", "Unexpected Output"</code></pre>
</section>
