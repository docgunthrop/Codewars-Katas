<!-- Hexagoku Solver -->
<p><a href='https://en.wikipedia.org/wiki/Sudoku' style='color:#9f9;text-decoration:none'>Sudoku</a> is a popular puzzle game that consists of populating a 9 x 9 square grid with an equal number of the nine integers in the range <code>1</code> through <code>9</code>.<br/><br/>
Now what if we wanted to use a different kind of grid? In this kata, we present such a challenge using a hexagon-based grid. We'll call it <strong style='color:#8df'>Hexagoku</strong>.</p>

<p>Your task is to write a function that receives a positive integer and a list of integer pairs and returns a 2-dimensional list representing a hexagonal grid populated by integers.
</p>

<img src='https://i.imgur.com/dPNCLI2.png'/>
<sup style='color:#ccc'>The image above represents the grid of our example test case</sup>

<h2 style='color:#f88'>Puzzle Success Conditions</h2>
<ul>
<li>Like Sudoku, this grid must be populated by integers from <code>1</code> through <code>9</code>, inclusive</li>
<li>Unlike Sudoku, there will be one <code>0</code> integer that occupies exactly <code>1</code> cell</li>
<li>Each integer on the grid must <b>not</b> have a duplicate in the same direction of any of the 6 sides of the cell it occupies</li>
<li>Each integer must appear the same number of times on the grid (except for <code>0</code> which only appears once)</li>
</ul>

<h2 style='color:#f88'>Input Specification</h2>
<ul>
<li>Your function will receive <code>2</code> arguments:<br/>
	<ul>
	<li><code>n</code>: the length of the grid's side (it will always be 3 or 4)</li>
	<li><code>arr</code>: a list comprised of <code>10</code> integer pairs</li>
	</ul>
</li>
<li>Each element in <code>arr</code> will be an integer pair <code>[x,y]</code> where <code>x</code> is its row position and <code>y</code> is its column position</li>
<li>Each element's index position represents its integer value.<br/>In our test example, the pair at index <code>1</code> is <code>[3,2]</code>; this means there is a <code>1</code> at row 3, column 2 on the hexagonal grid</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>

<pre><code>Below is pseudocode; refer to the initial test setup for your language

Example Arguments
-----------------
n = 4
arr = [ [2,2], [3,2], [3,5], [6,2], [0,3], [3,3], [0,0], [6,1], [4,0], [2,5] ]

Here n is given as 4, so each side of the hexagonal grid is 4 cells wide which means the grid consists of 37 cells.
Therefore each positive integer should appear 4 times.

The example arguments give us the initial state of the puzzle, as shown below.
Note that a "row" in this context is defined as a horizontal row, and the column value of a cell is its
position in its respective row starting from the left-most cell.

<span style='color:#bebdf9'>   6</span><span style='color:#999'> ? ? </span><span style='color:#ff2814'>4</span>
<span style='color:#999'>  ? ? ? ? ?</span>
<span style='color:#999'> ? ?</span> <span style='color:#fff'>0</span> <span style='color:#999'>? ?</span> <span style='color:#ff9054'>9</span>
<span style='color:#999'>? ?</span> <span style='color:#00ffff'>1</span> <span style='color:#e6e600'>5</span> <span style='color:#999'>?</span> <span style='color:#4ae84c'>2</span> <span style='color:#999'>?</span>
<span style='color:#e8bb8e'> 8</span> <span style='color:#999'>? ? ? ? ?</span>
<span style='color:#999'>  ? ? ? ? ?</span>
<span style='color:#999'>   ?</span> <span style='color:#d761e1'>7</span> <span style='color:#4499ff'>3</span> <span style='color:#999'>?</span>

Our example solution below is one among the multiple valid solutions that meet the conditions required to pass.

example_solution = [
	[    6,9,8,4    ],
	[   2,3,7,6,5   ],
	[  8,6,0,3,1,9  ],
	[ 7,4,1,5,6,2,3 ],
	[  8,5,9,2,4,7  ],
	[   9,2,4,1,5   ],
	[    1,7,3,8    ]
]

hexagoku(n,arr) == example_solution
</code></pre>

<h2 style='color:#f88'>Test Specifications</h2>
<ul>
<li>All inputs will be valid</li>
<li>All tests will be solvable</li>
<li>A preloaded function <code>print_grid</code> is provided to print your output in hexagon form</li>
<li>The exact type of input/output is language-dependent (e.g. array for JavaScript, tuple for Python, etc.)</li>
<li>Full Test Suite: <code>10</code> fixed tests and <code>10</code> random tests</li>
<li>For JavaScript, <code>module</code> and <code>require</code> are disabled</li>
</ul>

<p><span style='color:#f88'><b>Note on Hexagoku Concept:</b></span> The puzzle that is Hexagoku is an original concept. To the best of my knowledge, this puzzle has not existed before this kata.</p>

<p><a href='https://www.codewars.com/kata/5ecc1d68c6029000017d8aaf' style='color:#9f9;text-decoration:none'>Interested in trying another hexagon grid-based puzzle kata?</a></p>

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
