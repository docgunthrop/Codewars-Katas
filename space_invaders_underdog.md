<p style='font-size:0.9em'><i>This kata is inspired by <a href="https://en.wikipedia.org/wiki/Space_Invaders" style="color:#9f9;text-decoration:none"><b>Space Invaders</b></a> (Japanese: スペースインベーダー), an arcade video game created by Tomohiro Nishikado and released in 1978.</i></p>

<p>Alien invaders are attacking Earth and you've been conscripted to defend.<br>
<span style='color:#8df'>The Bad News:</span> You performed poorly in the manual training. As a result, you're ranked low priority and you're piloting a space jalopy.<br>
<span style='color:#8df'>The Good News:</span> Your coding skill is better than your piloting and you know the movement pattern of the alien spaceships.</p>

<p>You're going to program an algorithm that aids in shooting down the incoming alien wave despite your limitations.</p>

<h2 style='color:#f88'>Input</h2>
<p>The action takes place on an <code>m</code> x <code>n</code> matrix. Your function will receive two arguments:</p>
<ul>
	<li>a 2-D array where each subarray represents a row of alien ships. Subarrays consist of integers that represent each alien ship. Zero values (<code>0</code>) are empty spaces.
	</li>
	<li>your <code>[row,column]</code> coordinates</li>
</ul>
<p>The width (<code>n</code>) of a row is equal to the length of a subarray in the first argument and all rows are of the same length.<br>
Your <code>row</code> coordinate will be the last row of the matrix (<code>m - 1</code>).</p>

<p><span style='color:#f88'><b>Alien Ship Movement Pattern</b></span><br>
<ul>
	<li>Each alien ship is given in the form of an integer that represents its movement speed and direction.</li>
	<li><b>Alien ships move left or right.</b> A positive integer means an alien moves right, a negative integer means an alien moves left. The absolute value of the integer is the distance the alien moves in <code>1</code> turn.</li>
	<li>When an alien reaches an edge, it moves down one position and reverses lateral (left/right) direction.</li>
</ul>

<p><span style='color:#f88'><b>Your Ship's Limitations</b></span><br>
<ul>
	<li>Your position is fixed.</li>
	<li>Your pulse cannon has a time delay of <code>1</code> turn. After the delay, your cannon blasts the first target in its path.</li>
	<li>You can fire up to one shot per turn.</li>
</ul>
</p>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return an array of integers. Each integer represents the turn for each shot fired from your ship's cannon. If it is not possible to destroy all alien ships before they reach the last row, return <code>null</code> or <code>None</code>.</p>

<h2 style='color:#f88'>Test Example</h2>
<div style="background:#262729"><img src="https://i.imgur.com/S4qYQQ0.png" alt="state 0"></div>
<p><span style='color:#9f9'><b>Above:</b></span> Turn 0 (Initial State)<br>
<span style='color:#9f9'><b>Below:</b></span> Turn 1</p>
<div style="background:#262729"><img src="https://i.imgur.com/Iah7dQc.png" alt="state 1"></div>
<p>The images above represent the matrix states at Turn <code>0</code> and Turn <code>1</code> for the test example below. Note the following:</p>
<ul>
	<li><b>Multiple alien ships can occupy the same space concurrently.</b> The red alien at <code>[0,2]</code> and the light blue alien at <code>[0,7]</code> at turn <code>0</code> will both end up at position <code>[0,4]</code> at turn <code>1</code>.</li>
	<li>The pink alien (<code>1</code>) at <code>[0,9]</code> at turn <code>0</code> is already at the right edge, so it moves one space down and changes direction from right to left.</li>
	<li>The yellow alien (<code>6</code>) at <code>[0,6]</code> at turn <code>0</code> ends up at <code>[1,7]</code> at turn <code>1</code>.</li>
	<li>The green alien (<code>7</code>) at <code>[0,8]</code> at turn <code>0</code> ends up at <code>[1,4]</code> (white alien) and gets shot down by your cannon at turn <code>1</code>. Therefore, the time of registering your first shot is at turn <code>0</code>.</li>
</ul>

<p>In the test example, there is only one subarray in the first argument, meaning only the top row (row <code>0</code>) of the matrix is occupied at the initial state.</p>

```javascript
const alienWave = [[3,1,2,-2,2,3,6,-3,7,1]];
const position = [6,4];

blastSequence(alienWave,position);// [0, 2, 3, 4, 5, 9, 10, 13, 19, 22]
```
```python
alien_wave = [[3,1,2,-2,2,3,6,-3,7,1]]
position = [6,4]

blast_sequence(alien_wave,position)# [0, 2, 3, 4, 5, 9, 10, 13, 19, 22]
```
```java
int[][] alien_wave = {{3,1,2,-2,2,3,6,-3,7,1}};
int[] position = {6,4};

new SpaceInvaders(alien_wave,position).blastSequence(); # [0, 2, 3, 4, 5, 9, 10, 13, 19, 22]
```

<h3 style='color:#f88'>Other Technical Details</h3>
<ul>
	<li>In the event where multiple alien ships occupy the same position and the position is the target of your cannon fire, the fastest alien ship will be destroyed. If two ships are going at the same speed in opposite directions, the ship moving to the right will be destroyed.</li>
	<li>All alien ship movement speeds will be less than the width of the matrix.</li>
	<li>Alien count upper bound is <code>228</code></li>
	<li>Inputs will always be valid</li>
</ul>

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
