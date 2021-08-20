---
type: "reveal"
hidden: true
---
<section>
    <h3>Python Function</h3>
    <pre class="python" style="font-size: 50px"><code>def addition(x, y):
    return x + y</code></pre>
    <h3>Python Lambda</h3>
    <pre class="python" style="font-size: 50px"><code>addition_lambda = lambda x, y: x + y</code></pre>
    <ul>
        <li><code>lambda</code> keyword</li>
        <li>Parameters list<br>(any valid Python parameters)</li>
        <li><b>Single expression</b></li>
    </ul>
</section>
<section>
    <h3>Python Lambda</h3>
    <pre class="python stretch" style="font-size: 30px"><code>class Calculator:<br>
    @staticmethod
    def addition(x, y):
        return x + y<br>
    def operate_binary(self, a, b, operation):
        return operation(a, b)<br>
    @staticmethod
    def main():
        calc = Calculator()
        subtraction = lambda x, y: x - y
        print("40 + 2 = {}".format(calc.operate_binary(40, 2, Calculator.addition)))
        print("20 - 10 = {}".format(calc.operate_binary(20, 10, subtraction)))
        print("7 * 6 = {}".format(calc.operate_binary(7, 6, lambda: x, y: x * y)))<br>
if __name__ == "__main__":
    Calculator.main()</code></pre>
</section>
<section>
    <h3>Python Lambda</h3>
    <pre class="python stretch" style="font-size: 42px"><code>def process_persons(roster, filter, mapper, action):
    for p in roster:
        if filter(p):
            data = mapper(p)
            action(data)<br><br>
process_persons(roster,
                lambda p: (p.gender == MALE and
                           p.age >= 18 and
                           p.age <= 25),
                lambda p: p.email_address,
                lambda p: print(email))</code></pre>
</section>
