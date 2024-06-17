---
type: "reveal"
hidden: true
---
<section>
    <h3>Java Swing</h3>
    <img class="plain stretch" src="/cc410/images/9/410_9_swing.png">
    <p class="imagecredit">Image Credit: <a href="https://commons.wikimedia.org/w/index.php?title=File:Gui-widgets.png&oldid=458387263">Wikipedia</a></p>
</section>
<section>
    <h3>Java Swing</h3>
    <ul>
        <li>Developed in late 1990s</li>
        <li>Upgrade to<br>
            Abstract Window Toolkit (AWT)</li>
        <li>Object-Oriented, Inheritable</li>
        <li>Change Look and Feel</li>
        <li>Cross-Platform</li>
    </ul>
</section>
<section>
    <h3>Imports</h3>
    <pre class="java"><code>import java.awt.*;
import java.awt.event.*;
import javax.swing.*;</code></pre>
</section>
<section>
    <h3>Class Structure</h3>
    <pre class="java stretch"><code>public class MainWindow extends JFrame 
                        implements ActionListener {<br>
    public MainWindow() {
        // create GUI
    }<br>
    @Override
    public void actionPerformed(ActionEvent e) {
        // handle events
    }<br>
    public static void main(String[] args){
        // start program
    }
}</code></pre>
</section>
<section>
    <h3>Layout</h3>
    <pre class="java stretch"><code>// sets the size of this window
this.setSize(new Dimension(200, 100));<br>
// tell the program to exit when this window is closed
this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);<br>
// set the layout manager
this.setLayout(new GridBagLayout());<br>
// Create the constraints for the GridBagLayout manager
GridBagConstraints gbc = new GridBagConstraints();</code></pre>
</section>
<section>
    <h3>GridBagLayout</h3>
    <img class="plain stretch" src="/cc410/images/9/410_9_gridbag1.png">
    <p class="imagecredit">Image Credit: <a href="https://docs.oracle.com/javase/tutorial/uiswing/layout/gridbag.html">Oracle</a></p>
</section>
<section>
    <h3>GridBagLayout</h3>
    <p>Uses Rows & Columns</p>
    <img class="plain stretch" src="/cc410/images/9/410_9_gridbag2.jpg">
    <p class="imagecredit">Image Credit: <a href="https://docs.oracle.com/javase/tutorial/uiswing/layout/gridbag.html">Oracle</a></p>
</section>
<section>
    <h3>GridBagLayout</h3>
    <p>Can Grow to Fit Screen</p>
    <img class="plain stretch" src="/cc410/images/9/410_9_gridbag3.png">
    <p class="imagecredit">Image Credit: <a href="https://docs.oracle.com/javase/tutorial/uiswing/layout/gridbag.html">Oracle</a></p>
</section>
<section>
    <h3>Label</h3>
    <pre class="java"><code>// set the constraints for the label
gbc.fill = GridBagConstraints.HORIZONTAL;
gbc.gridx = 0;
gbc.gridy = 0;<br>
// add a label
this.add(new JLabel("Hello World!"), gbc);</code></pre>
</section>
<section>
    <h3>Button</h3>
    <pre class="java stretch"><code>// reset the constraints for the button
gbc.gridx = 0;
gbc.gridy = 1;<br>
// create a button 
JButton button = new JButton("Close");
// set the button's command:
button.setActionCommand("close");
// send the clicked event to this object
button.addActionListener(this);
// add the button
this.add(button, gbc);</code></pre>
</section>
<section>
    <h3>Java Example</h3>
    <img class="plain" width="500px" src="/cc410/images/9/410_9_javahello.png">
</section>
<section>
    <h3>Handle Events</h3>
    <p>Specified by <code>ActionListener</code> interface</code></p>
    <pre class="java" style="font-size: 37px"><code>@Override
public void actionPerformed(ActionEvent e) {
    if ("close".equals(e.getActionCommand())) {
        // close button was clicked, so exit the application
        System.exit(0);
    }
}</code></pre>
</section>
<section>
    <h3>Start Application</h3>
    <p>Use a Thread!</p>
    <pre class="java" style="font-size: 37px"><code>public static void main(String[] args){
    SwingUtilities.invokeLater(new Runnable() {
        public void run() {
            new MainWindow().setVisible(true);
        }
    });
}</code></pre>
</section>