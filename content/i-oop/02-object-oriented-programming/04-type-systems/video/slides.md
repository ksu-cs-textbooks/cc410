---
type: "reveal"
hidden: true
---
<section>
	<h2>Types</h2>
    <table>
        <tr>
            <th>Data</th>
            <th>Java</th>
            <th>Python</th>
        </tr>
        <tr>
            <td>Whole Numbers</td>
            <td>int</td>
            <td>int</td>
        </tr>
        <tr>
            <td>Floating Point</td>
            <td>double</td>
            <td>float</td>
        </tr>
        <tr>
            <td>Boolean</td>
            <td>boolean</td>
            <td>bool</td>
        </tr>
        <tr>
            <td>Character</td>
            <td>char</td>
            <td>str*</td>
        </tr>
        <tr>
            <td>Strings</td>
            <td>String*</td>
            <td>str</td>
        </tr>
    </table>
</section>
<section>
    <p>Classes (structs) are simply new types that group together these primitive types to store related data</p>
    <h4 class="fragment">Everything is a primitive</h4>
    <h4 class="fragment">A class is a new type</h4>
</section>
<section>
    <h2>Type Systems</h2>
    <ul>
        <li><b>Static</b> - type is specified at creation and a variable's type cannot change (Java)</li>
        <li><b>Dynamic</b> - type depends on data currently stored, and a variable may store different types (Python)</li>
    </ul>
</section>
<section>
    <h2>Type Systems</h2>
    <ul>
        <li><b>Strong</b> - the computer can determine what type of data a variable stores at all times<br>(Java & Python)</li>
        <li><b>Weak</b> - the computer cannot determine what type of data a variable stores (Assembly)</li>
    </ul>
</section>
<section>
    <h2>Java</h2>
    <p>Strong & Static</p>
    <h2>Python</h2>
    <p>Strong & Dynamic</p>
    <p class="fragment"><i>we will use type annotations<br>to make Python more static</i></p>
</section>