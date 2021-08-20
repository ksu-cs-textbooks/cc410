---
type: "reveal"
hidden: true
---
<section>
    <h3>Java Lambda</h3>
    <pre class="java" style="font-size: 70px"><code>(x, y) -> x + y;</code></pre>
    <ul>
        <li>Parameters in parentheses</li>
        <li>Arrow <code>-></code></li>
        <li>Statement or block with curly braces</li>
    </ul>
</section>
<section>
    <h3>Java Lambda</h3>
    <pre class="java stretch" style="font-size: 35px"><code>public class Calculator {<br>
    interface IntegerMath {
        int operation(int a, int b);   
    }<br>
    public int operateBinary(int a, int b, IntegerMath op) {
        return op.operation(a, b);
    }<br>
    public static void main(String... args) {
        Calculator myApp = new Calculator();
        IntegerMath addition = (a, b) -> a + b;
        IntegerMath subtraction = (a, b) -> a - b;
        System.out.println("40 + 2 = " +
            myApp.operateBinary(40, 2, addition));
        System.out.println("20 - 10 = " +
            myApp.operateBinary(20, 10, subtraction));    
    }
}</code></pre>
</section>
<section>
    <h3>Java Lambda</h3>
    <pre class="java stretch" style="font-size: 32px"><code>public static void processPersonsWithFunction(
    List<Person> roster,
    Predicate<Person> tester,
    Function<Person, String> mapper,
    Consumer<String> block) {
    for (Person p : roster) {
        if (tester.test(p)) {
            String data = mapper.apply(p);
            block.accept(data);
        }
    }
}<br>
processPersonsWithFunction(
    roster,
    p -> p.getGender() == Person.Sex.MALE
        && p.getAge() >= 18
        && p.getAge() <= 25,
    p -> p.getEmailAddress(),
    email -> System.out.println(email)
);</code></pre>
</section>