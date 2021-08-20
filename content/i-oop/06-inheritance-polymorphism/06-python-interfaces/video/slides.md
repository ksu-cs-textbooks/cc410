---
type: "reveal"
hidden: true
---
<section>
    <h3>Python Interfaces</h3>
    <ul>
        <li>Set <code>metaclass=abc.ABCMeta</code></li>
        <li>Implement <code>__subclasshook__</code> method</li>
        <li>All methods and properties marked as <code>@abc.abstractmethod</code></li>
        <li>No attributes</li>
        <li>No constructor, no code</li>
    </ul>
</section>
<section>
    <h3>Python Interface Example</h3>
    <pre class="python stretch" style="font-size: 19px"><code>import abc
from typing import List<br><br>
class IMyQueue(metaclass=abc.ABCMeta):<br>
    @classmethod
    def __subclasshook__(cls, subclass: type) -> bool:
        if cls is IMyQueue:
            attrs: List[str] = ['size']
            callables: List[str] = ['enqueue', 'dequeue', 'peek']
            ret: bool = True
            for attr in attrs:
                ret = ret and (hasattr(subclass, attr) 
                            and isinstance(getattr(subclass, attr), property))
            for call in callables:
                ret = ret and (hasattr(subclass, call) 
                            and callable(getattr(subclass, call)))
            return ret
        else:
            return NotImplemented<br>
    @property
    @abc.abstractmethod
    def size(self) -> int:
        raise NotImplementedError<br>
    @abc.abstractmethod
    def enqueue(self, o: object) -> None:
        raise NotImplementedError<br>
    @abc.abstractmethod
    def dequeue(self) -> object:
        raise NotImplementedError<br>
    @abc.abstractmethod
    def peek(self) -> object:
        raise NotImplementedError<br>
</code></pre>
</section>
<section>
    <h3>Using a Python Interface</h3>
    <pre class="python stretch"><code>class WaitingList(IMyQueue):<br>
    @property
    def size(self) -> int:
        # code here<br>
    def enqueue(self, o: object) -> None:
        #code here<br>
    def dequeue(self) -> object:
        #code here<br>
    def peek(self) -> object:
        #code here<br>
</code></pre>
</section>
<section>
    <h3>Interfaces are Types</h3>
    <pre class="python"><code>wait: IMyQueue = WaitingList()
wait.enqueue(Person())
wait.dequeue()</pre></code>
    <p>We can call any methods<br>defined by the interface</p>
    <p>Python uses duck typing,<br>but Mypy wants a type</p>
</section>
<section>
    <h3>Python Inheritance</h3>
    <ul style="font-size: 70px;">
        <li>Subclass inherits all <b>state</b> and <b>behavior</b></li>
        <li>Subclass has all attributes and methods of superclass</li>
        <li>Subclass constructor can call <code>super()</code> constructor</li>
        <li>Subclass can <b>override</b> superclass methods with new code</li>
    </ul>
</section>
<section>
    <pre class="python stretch"><code>class Canine:
    def __init__(self) -> None:
        self._name = "Name"<br>
    def bark(self) -> None:
        # code here<br>
class Dog(Canine):
    def __init__(self) -> None:
        self._owner = "Owner"<br>
    def pet(self) -> None:
        # code here<br>
class GuideDog(Dog):
    def __init__(self) -> None:
        self._trainer = "Trainer"<br>
    def guide(self) -> None:
        # code here</code></pre>
</section>
<section>
    <h6>Subclass has all Superclass behaviors</h6>
    <pre class="python"><code>lassie: GuideDog = GuideDog()
lassie.bark()
lassie.pet()
lassie.guide()</code></pre>
</section>
<section>
    <h3>Multiple Inheritance</h3>
    <p>Classes in Python can inherit from any number of classes or interfaces</p>
    <p>It will have access to all superclass attributes and methods</p>
    <p>Be aware of name collisions!</p>
</section>