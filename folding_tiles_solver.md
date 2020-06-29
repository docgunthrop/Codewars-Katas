<!--Folding Tiles Solver-->
<p>This kata is inspired by a puzzle game for Android called <span style="color:#95c4ff">Folding Blocks</span> by Popcore Games. (video displayed below)</p>

<video controls="" autoplay="autoplay" loop="loop"><source src="https://giant.gfycat.com/AcademicPlayfulFunnelweaverspider.webm" type="video/webm"></video>

<h2 style='color:#f88'>Mechanics Overview</h2>
<img src='https://i.imgur.com/qUPpZlt.png'/>
<p>You are presented with a rectangular matrix (grid) containing some colored tiles <span style="color:#4d8">[0]</span><br/>
All tiles of a given color form a single <span style="color:light-blue">group</span>, even if some tiles are separate from others.<br/>
A group can replicate by "folding" a copy of itself in a cardinal direction, namely up, down, left, or right. Refer to the reference image for additional clarity.<br/>
Your goal is to write a function that returns a sequence of folds to completely fill a given grid with colored tiles <span style="color:#4d8">[9]</span></p>

<p><b>NOTE</b> that a fold can only occur if the positions of all the newly created cells are empty and remain within the confines of the grid.</p>

<h2 style='color:#f88'>Input</h2>
Your function will receive a single string as an argument. The string will consist of any combination of uppercase alphabetic letters, spaces, and newline characters. Their representations are as follows:
<ul>
<li>Each unique alphabetic letter represents its own unique color.</li>
<li>Spaces represent an empty tile space in the grid</li>
<li>Newline characters represent the delimiters between rows (and all rows are of equal length)</li>
</ul>

<h2 style='color:#f88'>Output</h2>
If a valid solution exists, your function should return a tuple comprised of strings. Each string should be two characters in length and must consist of only uppercase alphabetic letters. The 2nd character must be a directional letter from "UDLR" (for Up, Down, Left, and Right, respectively).

If there is no possible solution, return `null` or `None`.

<h2 style='color:#f88'>Test Example</h2>
<p>A graphic illustration of this test example is provided in the section <span style='color:#f88'>Mechanics Overview</span>, above. In our example solution, the first fold is given as <code>BL</code>, meaning that the group of tiles of color <code>B</code> will fold to the <code>Left</code>, resulting in frame <code>[1]</code> in the illustration above (the new tiles created from the fold are displayed with thick white borders)</p>

```python
example = '\n'.join((
	'AAA   ',
	' A    ',
	'   B B',
	'      ',
	'  C D ',
	'      '
))

# This is just one of multiple valid solutions
solver(example)# ('BL','BU','AR','AD','CR','CL','CD','DD','DR')
```

```javascript
const example = [
	'AAA   ',
	' A    ',
	'   B B',
	'      ',
	'  C D ',
	'      '
].join('\n');

// This is just one of multiple valid solutions
solver(example)// ['BL','BU','AR','AD','CR','CL','CD','DD','DR']
```

<h2 style='color:#f88'>Additional Details</h2>

- The maximum number of unique colors for any given test is `6`
- The vertical and horizontal lengths of the grid are in the range: `2 <= length <= 12`
- Test cases will have `0` or more possible solutions
- Full Test Suite: `16` fixed tests and `46` random tests
- Use Python 3+ for the Python translation
<!-- - For JavaScript, many built-in prototypes are frozen, except `Array` -->
- All inputs will be valid

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
