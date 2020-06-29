<!-- Hexagon Beam Max Sum -->
<p>In this kata, your task is to find the maximum sum of any straight "beam" on a hexagonal grid, where its cell values are determined by a finite integer sequence <code>seq</code>.<br/><br/>
In this context, a beam is a linear sequence of cells in any of the 3 pairs of opposing sides of a hexagon. We'll refer to the sum of a beam's integer values as the "beam value".<br/>Refer to the example below for further clarification.</p>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive two arguments:</p>
<ul>
<li><code>n</code> : the length of each side of the hexagonal grid, where <code>2 <= n < 100</code></li>
<li><code>seq</code> : a finite sequence of (positive and/or nonpositive) integers with a length >= 1<br/>The sequence is used to populate the cells of the grid and should be repeated as necessary.<br/>The sequence type will be dependent on the language (e.g. array for JavaScript, tuple for Python, etc.).</li>
</ul>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return the largest beam value as an integer.</p>


<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/9cL0hjt.png'/><br/>

<pre><code>In our test example, we have the following arguments:
n = 4
seq = [2, 4, 6, 8]

Below is the hexagonal grid determined by our example arguments;
the sequence repeats itself from left to right, then top to bottom.

   2 4 6 8
  2 4 6 8 2
 4 6 8 2 4 6
8 2 4 6 8 2 4
 6 8 2 4 6 8
  2 4 6 8 2
   4 6 8 2

The three diagrams below illustrate the "beams" in the hexagonal grid above.
In the grid on the left, the horizontal beams are highlighted by their likewise colors,
and the value of each beam is given to its right.
In the center grid, the beams highlighted go from upper-right to bottom-left (and vice-versa).
In the grid on the right, the beams highlighted go from upper-left to bottom-right (and vice-versa).

<span style='color:#00ff00'>   2 4 6 8</span> -> 20        <span style='color:#00ff00'>   2</span> <span style='color:#00f0f0'>4</span> <span style='color:#f0f000'>6</span> <span style='color:#ff3030'>8</span>        <span style='color:#ff3030'>   2</span> <span style='color:#9090ff'>4</span> <span style='color:#f000f0'>6</span> <span style='color:#a0a0a0'>8</span>
<span style='color:#00f0f0'>  2 4 6 8 2</span> -> 22       <span style='color:#00ff00'>  2</span> <span style='color:#00f0f0'>4</span> <span style='color:#f0f000'>6</span> <span style='color:#ff3030'>8</span> <span style='color:#9090ff'>2</span>       <span style='color:#f0f000'>  2</span> <span style='color:#ff3030'>4</span> <span style='color:#9090ff'>6</span> <span style='color:#f000f0'>8</span> <span style='color:#a0a0a0'>2</span>
<span style='color:#f0f000'> 4 6 8 2 4 6</span> -> 30      <span style='color:#00ff00'> 4</span> <span style='color:#00f0f0'>6</span> <span style='color:#f0f000'>8</span> <span style='color:#ff3030'>2</span> <span style='color:#9090ff'>4</span> <span style='color:#f000f0'>6</span>      <span style='color:#00f0f0'> 4</span> <span style='color:#f0f000'>6</span> <span style='color:#ff3030'>8</span> <span style='color:#9090ff'>2</span> <span style='color:#f000f0'>4</span> <span style='color:#a0a0a0'>6</span>
<span style='color:#ff3030'>8 2 4 6 8 2 4</span> -> 34     <span style='color:#00ff00'>8</span> <span style='color:#00f0f0'>2</span> <span style='color:#f0f000'>4</span> <span style='color:#ff3030'>6</span> <span style='color:#9090ff'>8</span> <span style='color:#f000f0'>2</span> <span style='color:#a0a0a0'>4</span>     <span style='color:#00ff00'>8</span> <span style='color:#00f0f0'>2</span> <span style='color:#f0f000'>4</span> <span style='color:#ff3030'>6</span> <span style='color:#9090ff'>8</span> <span style='color:#f000f0'>2</span> <span style='color:#a0a0a0'>4</span>
<span style='color:#9090ff'> 6 8 2 4 6 8</span> -> 34      <span style='color:#00f0f0'> 6</span> <span style='color:#f0f000'>8</span> <span style='color:#ff3030'>2</span> <span style='color:#9090ff'>4</span> <span style='color:#f000f0'>6</span> <span style='color:#a0a0a0'>8</span>      <span style='color:#00ff00'> 6</span> <span style='color:#00f0f0'>8</span> <span style='color:#f0f000'>2</span> <span style='color:#ff3030'>4</span> <span style='color:#9090ff'>6</span> <span style='color:#f000f0'>8</span>
<span style='color:#f000f0'>  2 4 6 8 2</span> -> 22       <span style='color:#f0f000'>  2</span> <span style='color:#ff3030'>4</span> <span style='color:#9090ff'>6</span> <span style='color:#f000f0'>8</span> <span style='color:#a0a0a0'>2</span>       <span style='color:#00ff00'>  2</span> <span style='color:#00f0f0'>4</span> <span style='color:#f0f000'>6</span> <span style='color:#ff3030'>8</span> <span style='color:#9090ff'>2</span>
<span style='color:#a0a0a0'>   4 6 8 2</span> -> 20        <span style='color:#ff3030'>   4</span> <span style='color:#9090ff'>6</span> <span style='color:#f000f0'>8</span> <span style='color:#a0a0a0'>2</span>        <span style='color:#00ff00'>   4</span> <span style='color:#00f0f0'>6</span> <span style='color:#f0f000'>8</span> <span style='color:#ff3030'>2</span>

The maximum beam value in our example is 34.
</code></pre>

<h2 style='color:#f88'>Test Specifications</h2>
<ul>
<li>All inputs will be valid</li>
<li>Full Test Suite: <code>12</code> fixed tests and <code>100</code> random tests</li>
<li>For JavaScript, <code>module</code> and <code>require</code> are disabled [NOTE: if you would like to suggest a module that you think should be permitted for JS, please leave a note in the Discourse section]</li>
</ul>

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
