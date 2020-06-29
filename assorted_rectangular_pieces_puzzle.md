<!-- Assorted Rectangular Pieces Puzzle -->
<p>You are given an assortment of rectangular pieces and a square board with holes in it. You need to arrange the pieces on the board so that all the pieces fill up the holes in the board with no overlap.</p>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive two arguments:</p>
<ul>
	<li><code style='color:#8df'>board</code> : an array/list of length <code>n</code> where each element is a string of length <code>n</code> consisting of <code>0</code>s and/or spaces. Each contiguous cluster of <code>0</code>s represents a hole in the board.</li>
	<li><code style='color:#8df'>pieces</code> : an array/list where each element is in the form <code>[h,w]</code> where <code>h</code> and <code>w</code> represent the height and width of each piece, respectively.
</ul>

<h2 style='color:#f88'>Output</h2>
<p>An array with the position of each piece to solve the puzzle. Each element should be an array in the form <code>[x,y,z]</code> where:</p>
<ul>
	<li><code>x</code> and <code>y</code> represents the piece's top-left corner position, as illustrated in the example below</li>
	<li><code>z</code> represents the orientation of the piece -- normal or rotated <code>90</code> degrees. If rotated, <code>z</code> is <code>1</code>, otherwise it's <code>0</code></li>
	<li>Each piece corresponds to the element from <code>pieces</code> with the same index position</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>
<p>Figure <code style='color:#f66'>A</code>: initial state of the puzzle board.<br/>Figure <code style='color:#f66'>B</code>: one possible configuration. Note that the number in each rectangle indicates its index in the input array.</p>
<img src="https://i.imgur.com/NCHwdqW.png" alt="example image"><br/>

```javascript
let board = [
	'            ',
	' 00000      ',
	' 00000      ',
	' 00000   00 ',
	'       000  ',
	'   00  000  ',
	' 0000 00    ',
	' 0000 00    ',
	' 00   000 0 ',
	'      000 0 ',
	'  0       0 ',
	'000         '
];
let pieces = [[1,1], [1,1], [1,2], [1,2], [1,2], [1,3], [1,3], [1,4], [1,4], [2,2], [2,2], [2,3], [2,3], [2,5]];

solve_puzzle(board,pieces); // [[11,0,0],[11,1,0],[1,1,0],[3,9,0],[10,2,1],[1,3,0],[8,10,1],[4,7,1],[6,6,1],[4,8,0],[8,7,0],[5,3,1],[6,1,1],[2,1,0]]
```
```python
board = [
	'            ',
	' 00000      ',
	' 00000      ',
	' 00000   00 ',
	'       000  ',
	'   00  000  ',
	' 0000 00    ',
	' 0000 00    ',
	' 00   000 0 ',
	'      000 0 ',
	'  0       0 ',
	'000         '
]
pieces = [[1,1], [1,1], [1,2], [1,2], [1,2], [1,3], [1,3], [1,4], [1,4], [2,2], [2,2], [2,3], [2,3], [2,5]]

solve_puzzle(board,pieces); # [[11,0,0],[11,1,0],[1,1,0],[3,9,0],[10,2,1],[1,3,0],[8,10,1],[4,7,1],[6,6,1],[4,8,0],[8,7,0],[5,3,1],[6,1,1],[2,1,0]]
```

<h2 style='color:#f88'>Technical Constraints</h2>
<ul>
	<li>Each test will have one or more possible solutions</li>
	<li>Every piece must be used to solve the puzzle</li>
	<li>Every piece is a rectangle with height and width in the range: <code>12 >= x >= 1</code></li>
	<li>Number of pieces: <code>70 >= pieces >= 1</code></li>
	<li><code>n</code> x <code>n</code> board dimensions: <code>24 >= n >= 4</code></li>
	<li>Full Test Suite: <code>15</code> fixed tests, <code>60</code> random tests</li>
	<li>Efficiency is necessary to pass</li>
	<li>JavaScript: prototypes have been frozen and <code>require</code> has been disabled</li>
</ul>

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
