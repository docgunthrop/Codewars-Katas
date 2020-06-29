<!--Transforming Maze Solver-->
The objective of this kata will be to guide a ball through an `m` x `n` rectangular maze. This maze is special in that:
- all the cells rotate `90` degrees clockwise, in unison, at each interval
- each cell can have anywhere from `0` to `4` walls

<p>Your goal is to write a function that returns a path that requires the fewest intervals for the ball to get from its starting position to a specified destination.</p>


<h2 style='color:#f88'>Input</h2>
<p>Your function will receive one argument — an <code>m</code> x <code>n</code> matrix.</p>


<h2 style='color:#f88'>Output</h2>
<p>Your function must return a path as an array/list of strings. Each string in the array will:</p>
<ul>
	<li>consist only of the letters <code>N</code>, <code>W</code>, <code>S</code>, and <code>E</code> representing the directions <code>north</code>, <code>west</code>, <code>south</code>, and <code>east</code>, respectively</li>
	<li>represent the path of the ball at each interval (based on its index position in the array)</li>
</ul>

<p>Also note that empty strings are permitted in the output array.</br>
If there is no possible solution, return <code>null</code> or <code>None</code>.</p>


<h2 style='color:#f88'>Maze Mechanics</h2>
<p>Each cell in the maze is given as an integer, ranging from <code>0</code> to <code>15</code>. This number, when translated to binary form, represents the walls of the corresponding cell. That is, a <code>1</code> means there is a wall and a <code>0</code> means there is no wall. The order of the walls is north, west, south, and east.</p>

<p>For example, a cell with the value <code>7</code> is <code>0111</code> in binary. This means it has 3 walls — initially on the west, south, and east sides. Since there is no wall on the north side of the cell, it can be entered from that side at time interval <code>0</code> (assuming that the adjacent cell to its north does not have a south wall).</p>

<p>A cell with the value <code>5</code> (<code>0101</code> in binary) can be entered from its north and south sides at interval <code>0</code>. At the next interval, it rotates <code>90</code> degrees clockwise and can then only be entered from its west and east sides (<code>1010</code>).</p>

<p>A cell with the value <code>15</code> is enclosed on all sides (<code>1111</code> in binary) and therefore can never be entered. Likewise, a cell with a value of <code>0</code> can always be entered from any side.</p>

<p><b style='color:#8df'>There will be</b> <code>2</code> <b style='color:#8df'>cells that will not be given in the form of an integer.</b> Assume that these cells have no walls (the equivalent of a <code>0</code> cell):</p>
<ul>
	<li>The ball's starting position, given as the letter <code>B</code> (Java:<code>-1</code>)</li>
	<li>The destination, given as the letter <code>X</code> (Java:<code>-2</code>)</li>
</ul>


<h2 style='color:#f88'>Test Example</h2>

<img src='https://i.imgur.com/N1D2rcI.png'/>
<p>The image above shows the state of the maze and starting position of the ball at each each interval; the order is given in the bottom right square.</br>
The green shaded area shows the available cells the ball can move to at each interval, but the bold number shows where it ends up (for our example solution)
</p>

```python
example = (
	(  4,  2,  5,  4),
	(  4, 15, 11,  1),
	('B',  9,  6,  8),
	( 12,  7,  7,'X')
)

maze_solver(example) # ['NNE','EE','S','SS']
```

```javascript
let example = [
	[  4,  2,  5,  4],
	[  4, 15, 11,  1],
	['B',  9,  6,  8],
	[ 12,  7,  7,'X']
];

mazeSolver(example) // ['NNE','EE','S','SS']
```

<h2 style='color:#f88'>Technical Details</h2>
<ul>
	<li>The width and length of the matrix will range between <code>4</code> and <code>25</code> in either direction</li>
	<li>The ball's starting position will always be on the west side and the exit will always be on the east side of the maze</li>
	<li>For the sake of efficiency, the ball must not enter the same cell more than once per interval</li>
	<li>Full Test Suite: <code>10</code> fixed tests, and <code>110</code> random tests for Python / <code>100</code> random tests for JavaScript / <code>200</code> random tests for Java</li>
	<li>Each test case may have <code>0</code> or more possible solutions</li>
	<li>Inputs will always be valid</li>
	<li>Use Python 3+ for the Python translation</li>
	<li>For JavaScript, <code>require</code> has been disabled and most built-in prototypes have been frozen (prototype methods can be added to <code>Array</code>, <code>Function</code>, and <code>Set</code>)</li>
</ul>

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
