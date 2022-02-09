---
type: "reveal"
hidden: true
---
<section>
    <h3>Python tkinter</h3>
    <img class="plain stretch" src="/images/9/410_9_tk.png">
    <p class="imagecredit">Image Credit: <a href="https://commons.wikimedia.org/w/index.php?title=File:Tk-Demo_using_Tk_8.6.6_on_Windows_10,_November_2016.png&oldid=475248301">Wikipedia</a></p>
</section>
<section>
    <h3>Python tkinter</h3>
    <ul>
        <li>Python wrapper for Tk</li>
        <li>Developed in early 1990s</li>
        <li>Object-Oriented, Inheritable</li>
        <li>Change Look and Feel</li>
        <li>Cross-Platform</li>
    </ul>
</section>
<section>
    <h3>Imports</h3>
    <pre class="python"><code>import tkinter as tk
# themed widgets
from tkinter import ttk</code></pre>
</section>
<section>
    <h3>Class Structure</h3>
    <pre class="python stretch"><code>class MainWindow(tk.Tk):<br>
    def __init__(self) -> None:
        # create GUI<br>
    def action_performed(self, text: str) -> None:
        # handle events<br>
    @staticmethod
    def main(args: List[str]) -> None:
        # start program<br><br>
# Main Guard
if __name__ == "__main__":
    MainWindow.main(sys.argv)
</code></pre>
</section>
<section>
    <h3>Layout</h3>
    <pre class="python stretch"><code># Initialize the parent class
tk.Tk.__init__(self)<br>
# Set the window size
self.minsize(width=200, height=100)<br>
# Allow the grid to expand horizontally to fill the space
self.grid_rowconfigure(0, weight=1)
self.grid_rowconfigure(1, weight=1)
self.grid_columnconfigure(0, weight=1)</code></pre>
</section>
<section>
    <h3>Grid Geometry Manager</h3>
    <img class="plain stretch" src="/images/9/410_9_grid1.png">
    <p class="imagecredit">Image Credit: <a href="https://tkdocs.com/tutorial/grid.html">TkDocs</a></p>
</section>
<section>
    <h3>Grid Geometry Manager</h3>
    <p>Use <code>sticky</code> option to fill cell</p>
    <img class="plain stretch" src="/images/9/410_9_grid2.png">
    <p class="imagecredit">Image Credit: <a href="https://tkdocs.com/tutorial/grid.html">TkDocs</a></p>
</section>
<section>
    <h3>Grid Geometry Manager</h3>
    <p>Use <code>weight</code> option to stretch</p>
    <img class="plain stretch" src="/images/9/410_9_grid3.png">
    <p class="imagecredit">Image Credit: <a href="https://tkdocs.com/tutorial/grid.html">TkDocs</a></p>
</section>
<section>
    <h3>Grid Geometry Manager</h3>
    <p>Use <code>weight</code> option to stretch</p>
    <img class="plain stretch" src="/images/9/410_9_grid4.png">
    <p class="imagecredit">Image Credit: <a href="https://tkdocs.com/tutorial/grid.html">TkDocs</a></p>
</section>
<section>
    <h3>Label</h3>
    <pre class="python" style="font-size:40px"><code># Create a label and add it to the GUI
self.__label = tk.Label(master=self, text="Hello World!")
self.__label.grid(row=0, column=0)</code></pre>
</section>
<section>
    <h3>Button</h3>
    <pre class="python" style="font-size:38px"><code># Create a button and add it to the GUI
self.__button = tk.Button(master=self, text="Close",
                          command=lambda:
                          self.action_performed("close"))
self.__button.grid(row=1, column=0)</code></pre>
</section>
<section>
    <h3>Python Example</h3>
    <img class="plain" width="500px" src="/images/9/410_9_pythonhello.png">
</section>
<section>
    <h3>Handle Events</h3>
    <p>Specified by <code>lambda</code> expression</p>
    <pre class="python"><code>def action_performed(self, text: str) -> None:
    if text == "close":
        sys.exit(0)</code></pre>
</section>
<section>
    <h3>Start Application</h3>
    <p>Call the <code>mainloop()</code> method</p>
    <pre class="python" style="font-size: 37px"><code>@staticmethod
def main(args: List[str]) -> None:
    MainWindow().mainloop()</code></pre>
</section>