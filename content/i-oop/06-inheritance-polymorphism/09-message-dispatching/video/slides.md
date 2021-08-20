---
type: "reveal"
hidden: true
---
<section>
    <h3>Message Dispatch</h3>
    <ul>
        <li>Process of determining which version of a method to execute</li>
        <li>Java: method signature<br>(name and argument types)</li>
        <li>Python: method name only</li>
        <li>Based on the original object,<br>not data type</li>
    </ul>
</section>
<section>
    <div style="float: right; width: 40%">
        <h6>Python</h6>
        <pre class="python stretch" style="font-size: 28px"><code>class Canine:
    def bark(self) -> None:
        print("I'm scary")<br><br><br>
class Dog(Canine):
    def bark(self) -> None:
        print("I'm friendly")<br><br><br>
class GuideDog(Dog):
    def bark(self) -> None:
        print("I'm helpful")<br><br><br></code></pre>
    </div>
    <div style="float: left; width: 60%">
        <h6>Java</h6>
        <pre class="java stretch" style="font-size: 28px"><code>public class Canine {
    public void bark() {
        System.out.println("I'm scary");
    }
}<br>
public class Dog extends Canine {
    public void bark() {
        System.out.println("I'm friendly");
    }
}<br>
public class GuideDog extends Dog {
    public void bark() {
        System.out.println("I'm helpful");
    }
}</code></pre>
    </div>
</section>
<section>
    <h3>Message Dispatch</h3>
    <p>Depends on object, not data type</p>
    <div style="float: right; width: 50%">
        <h6>Python</h6>
        <pre class="python stretch" style="font-size: 35px"><code>dogs: List[Canine] = list()
dogs.append(Canine())
dogs.append(Dog())
dogs.append(GuideDog())
for dog in dogs:
    dog.bark()<br>
# I'm scary
# I'm friendly
# I'm helpful
</code></pre>
    </div>
    <div style="float: left; width: 50%">
        <h6>Java</h6>
        <pre class="java stretch" style="font-size: 35px"><code>Canine[] dogs = new Canine[3];
dogs[0] = new Canine();
dogs[1] = new Dog();
dogs[2] = new GuideDog();
for(Canine dog : dogs){
    dog.bark();
}
// I'm scary
// I'm friendly
// I'm helpful</code></pre>
    </div>
</section>
<section>
    <h3>Checking Type</h3>
    <div style="float: right; width: 50%">
        <h6>Python</h6>
        <pre class="python stretch" style="font-size: 32px"><code>if isinstance(dog, GuideDog):
    # treat dog like a GuideDog
</code></pre>
    </div>
    <div style="float: left; width: 50%">
        <h6>Java</h6>
        <pre class="java stretch" style="font-size: 32px"><code>if (dog instanceof GuideDog) {
    // cast dog to GuideDog type
    GuideDog gDog = (GuideDog) dog 
    // treat gDog as a GuideDog</code></pre>
    </div>
</section>
<section>
    <h3>Best Practices</h3>
    <ul>
        <li>Use <b>inheritance</b> for state and behavior with "real" superclass</li>
        <li>Use <b>abstract</b> for state and behavior with "imaginary" superclass</li>
        <li>Use <b>interface</b> for behaviors only</li>
    </ul>
</section>