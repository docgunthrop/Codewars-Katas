<div style="width:504px;height:262px;background:#ddd;padding:2px">
<img src="https://i.imgur.com/XbW4CRw.jpg" alt="Super Puzzle Fighter II Turbo screenshot">
</div>
<p>This kata is inspired by the arcade puzzle game <a href="https://en.wikipedia.org/wiki/Super_Puzzle_Fighter_II_Turbo" style="color:#9f9;text-decoration:none"><b>Super Puzzle Fighter II Turbo</b></a> (seen above).</p>
<p>In the game <i>Super Puzzle Fighter II Turbo</i>, the player controls pairs of blocks (referred to as "Gems") that drop into a pit-like playfield.</p>
<p>In this kata, your objective is to write a function that, given a sequence of Gem pairs and movement instructions, will return the ending game state.</p>

<h2 style='color:#f66'>Game Mechanics</h2>
<div style="width:402px;height:402px;background:#000;padding:6px">
<img src="https://i.imgur.com/iKwTYr3.png" alt="gems1">
</div>
<ul>
	<li>The playfield is a matrix with <code>12</code> rows and <code>6</code> columns; it begins empty.</li>
	<li>Gems come in four different colors — red, blue, green, and yellow.</li>
	<li>Similar in style to other <a href="https://en.wikipedia.org/wiki/Tile-matching_video_game">tile-matching video games</a>, a pair of adjacent Gems will descend into the playfield. This pair can be moved left and right, and can be rotated clockwise and counter-clockwise. Once it lands onto an obstacle, the process repeats.<br/>
	If the pair lands on an obstacle, but one of the Gems has empty space below it, the pair will disjoint and the unsupported Gem will continue to descend until it lands onto an obstacle.<br/>
	In the image above (left), the green-blue Gem pair inside the white rectangular outline will disjoint, with the green Gem merging with the green Power Gem and the blue Gem landing on the yellow Gem, if allowed to drop straight down as is.
	</li>
	<li><strong style='color:#95c4ffff'>Power Gems:</strong> Adjacent clusters of same-colored Gems in rectangular shapes, that are <code>2 x 2</code> or greater in width and height, will merge into one larger solid Gem, known as a <b>Power Gem</b>. In the image above (left), the larger blue Gem located at the bottom left is a <code>4 x 4</code> Power Gem. The green Gem just above it is a <code>2 x 3</code> Power Gem. In the image to the right, the green Gem that falls merges with the green Power Gem, transforming it into a <code>2 x 4</code> Power Gem.</li>
	<li>Each Gem pair descends from the <b>Drop Alley</b>, which is the top of the fourth column from the left, as shown above with the Gem pair inside the white dashed rectangle.</li>
	<li><strong style='color:#95c4ffff'>Crash Gems</strong> are special Gems that, upon contact with a same-colored Gem, will destroy all connected Gems of the same color, including other Crash Gems of the same color. In the process, the Crash Gem will self-destruct.<br/>
	In the image above (left), a yellow Crash Gem (the yellow circle) is part of a descending Gem pair. If left to fall straight down as is, it will destroy all the connected yellow Gems, resulting in the image to the right. The blue Crash Gem remains until a blue Gem comes in contact with it.</li>
	<li><strong style='color:#95c4ffff'>Rainbow Gems</strong> are a rare type of special Gem that destroy all Gems that match the color of the Gem it lands on, while self-destructing in the process. If it lands on the floor of the playfield, no other Gems will be destroyed.</li>
	<li>When rotating a Gem pair, the 2nd Gem will rotate around the 1st Gem. In the image above (left), the yellow Crash Gem will rotate around the red Gem. Note that a rotation may cause a shift in lateral position if a Gem pair is touching the left or right wall (to keep the Gems within the boundaries of the playfield).</li>
	<li>All movements for a Gem pair occur above the playfield before being dropped.</li>
	<li>There is only one descending Gem pair in play at any given time.<br/>
	In the image above (left), the red-yellow Gem pair (inside the dashed-rectangle) would appear <b>after</b> the green-blue Gem pair (inside the solid rectangle) has already settled.</li>
</ul>

<h3 style='color:#f66'>Power Gem Formation Priority</h3>
<div style="width:402px;height:192px;background:#000;padding:6px">
<img src="https://i.imgur.com/AlihfOm.png" alt="gems4"></div>
<div style="width:402px;height:140px;background:#000;padding:6px">
<img src="https://i.imgur.com/A4rQKjU.png" alt="gems4a"></div>
<p><strong>When a cluster of same-colored individual gems are set to form a Power Gem, but there is more than one possible configuration, priority goes to the potential Power Gem that is higher in elevation.</strong><br/>
In the first image above, after the green gems shatter, one of two possible Power Gems (that share resources) can be formed: a <code>2 x 2</code> block as shown in the image to the right, or a <code>2 x 2</code> block resting on the playfield floor. The Power Gem in the image to the right is the end result because it is higher in elevation.<br/>
In the second image above, the individual red gems fall after the green gems (left image) have been cleared (middle image). The resulting Power Gem is shown on the right side, where the <code>2 x 3</code> forms due to its higher elevation.</p>
<div style="width:402px;height:140px;background:#000;padding:6px">
<img src="https://i.imgur.com/eAAoGlg.png" alt="gems4b"></div>
<p><strong>If two possible Power Gems with the same elevation can be formed, priority goes to the Power Gem that expands horizontally</strong><br/>
Above, a Rainbow Gem will land on the green gem (left), thereby destroying all green gems and allowing the individual red gems to fall (middle). Two possible Power Gems can form as a result, both having the same elevation. In this case, the result is the Power Gem on the right (as opposed to a <code>2 x 3</code> "vertical" Power Gem that occupies the 4th and 5th columns).</p>
<div style="width:402px;height:192px;background:#000;padding:6px">
<img src="https://i.imgur.com/selVttM.png" alt="gems3">
</div>
<p><strong>When a cluster of unmerged same-colored Gems drops and results in a merge, the individual Gems will combine before combining with Power Gems.</strong><br/>
In the image above (left), the green Crash Gem is about to eliminate the group of green Gems, allowing the 3 red Gems and 1 blue Gem to drop. The 3 red Gems will join the other 3 red Gems below, and form a <code>2 x 3</code> Power Gem before merging with the other <code>2 x 3</code> red Power Gem to its right, to finally become a <code>4 x 3</code> Power Gem. The result is the image to the right.</p>
<div style="width:402px;height:162px;background:#000;padding:6px">
<img src="https://i.imgur.com/fx1v67s.png" alt="gems2">
</div>
<p><strong>In the case where an existing Power Gem can expand by increasing vertically or horizontally, priority goes to horizontal growth.</strong><br/>
In the image above (left), a green Crash Gem is about to eliminate a cluster of green Gems, allowing the Gems above to drop and land on the remaining Gems below.<br/>
Since priority goes to horizontal growth, the <code>2 x 2</code> red Power Gem will become a <code>3 x 2</code> Power Gem instead of a <code>2 x 3</code> Power Gem. The result is shown on the right.</p>

<h3 style='color:#f66'>How Moves Work:</h3>
<ol style="padding-left:10px">
	<li>At the start of a move, a Gem pair appears above the playfield.</li>
	<li>The pair falls, and each Gem in the pair land on another Gem or the playfield floor.</li>
	<li>All effects (eg. Power Gem formation, gem shattering due to Crash Gems or Rainbow Gems) initiated by any Gems will occur simultaneously.</li>
	<li>If any Gems are cleared (by Crash Gems or Rainbow Gems) in the process leaving some Gems suspended in air, all suspended Gems fall and land together.</li>
	<li>While step 4 makes an effect, repeat steps 3 and 4</li>
</ol>
<!-- <p>NOTE: In the case where the effects of both a Rainbow gem and a Crash gem occur at the same time, the effects of the Rainbow gem occur before the Crash gem</p> -->
<p>Below, the green Gem will combine with other adjacent ones to form a Power Gem, and at the same time the blue Crash Gem will shatter along with the two blue Gems below. The result is the middle frame, rather than the last frame.</p>
<div style="width:404px;height:252px;background:#000;padding:6px">
<img src="https://i.imgur.com/OLKTmLc.png" alt="gems5">
</div>

<h2 style='color:#f66'>Input</h2>
<p>Your function will receive a 2-D array/list. Each subarray has a length of <code>2</code> and consists of:</p>
<ul>
	<li>a 2-character string representing a Gem pair</li>
	<li>a string of instructions for the Gem pair</li>
</ul>
<p>Each Gem is represented by the first letter of its color in uppercase — <code>R</code>, <code>B</code>, <code>G</code>, or <code>Y</code>.<br/>
Crash Gems are represented by the first letter of its color in lowercase.<br/>
A Rainbow Gem is represented as <code>0</code>.
</p>
<p>Movement Instructions are as follows:</p>
<ul>
	<li><code>L</code>: move left</li>
	<li><code>R</code>: move right</li>
	<li><code>A</code>: rotate counter-clockwise</li>
	<li><code>B</code>: rotate clockwise</li>
</ul>

<h2 style='color:#f66'>Output</h2>
<p>Your function will return the ending game state in the form of a string. The string should consist of all <code>12</code> rows joined by newline characters.<br/>
If at any point in the game a stack of Gems goes above the top row, terminate the process and return the game state before the last move. This applies to Crash Gems and Rainbow Gems as well; their position is taken into account before their effect.
</p>

<h2 style='color:#f66'>Test Example</h2>

```javascript
let instructions = [
	['BR','LLL'],
	['BY','LL'],
	['BG','ALL'],
	['BY','BRR'],
	['RR','AR'],
	['GY','A'],
	['BB','AALLL'],
	['GR','A'],
	['RY','LL'],
	['GG','L'],
	['GY','BB'],
	['bR','ALLL'],
	['gy','AAL']
];
let gameState = [
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'    R ',
	' R  YR',
	'RR  RB'
].join('\n');

puzzleFighter(instructions) === gameState; //true

/* STEP-BY-STEP MOVES SEQUENCE
   (GAME STATE at end of each of the first 5 moves)

 MOVE 1      MOVE 2      MOVE 3      MOVE 4      MOVE 5
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║ B    ║    ║ B    ║    ║ B    ║
║B     ║    ║BB    ║    ║BB    ║    ║BB    ║    ║BB  RR║
║R     ║    ║RY    ║    ║RYG   ║    ║RYG YB║    ║RYG YB║
*/
```
```python
instructions = [
	['BR','LLL'],
	['BY','LL'],
	['BG','ALL'],
	['BY','BRR'],
	['RR','AR'],
	['GY','A'],
	['BB','AALLL'],
	['GR','A'],
	['RY','LL'],
	['GG','L'],
	['GY','BB'],
	['bR','ALLL'],
	['gy','AAL']
]
game_state = '\n'.join([
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'    R ',
	' R  YR',
	'RR  RB'
])

puzzle_fighter(instructions) == game_state #True

''' STEP-BY-STEP MOVES SEQUENCE
   (GAME STATE at end of each of the first 5 moves)

 MOVE 1      MOVE 2      MOVE 3      MOVE 4      MOVE 5
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║ B    ║    ║ B    ║    ║ B    ║
║B     ║    ║BB    ║    ║BB    ║    ║BB    ║    ║BB  RR║
║R     ║    ║RY    ║    ║RYG   ║    ║RYG YB║    ║RYG YB║
'''
```
```ruby
instructions = [
	['BR','LLL'],
	['BY','LL'],
	['BG','ALL'],
	['BY','BRR'],
	['RR','AR'],
	['GY','A'],
	['BB','AALLL'],
	['GR','A'],
	['RY','LL'],
	['GG','L'],
	['GY','BB'],
	['bR','ALLL'],
	['gy','AAL']
]
game_state = [
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'    R ',
	' R  YR',
	'RR  RB'
].join("\n")

puzzle_fighter(instructions) == game_state   # true

''' STEP-BY-STEP MOVES SEQUENCE
   (GAME STATE at end of each of the first 5 moves)

 MOVE 1      MOVE 2      MOVE 3      MOVE 4      MOVE 5
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║ B    ║    ║ B    ║    ║ B    ║
║B     ║    ║BB    ║    ║BB    ║    ║BB    ║    ║BB  RR║
║R     ║    ║RY    ║    ║RYG   ║    ║RYG YB║    ║RYG YB║
'''
```
```java
String[][] instructions = {
	{'BR','LLL'},
	{'BY','LL'},
	{'BG','ALL'},
	{'BY','BRR'},
	{'RR','AR'},
	{'GY','A'},
	{'BB','AALLL'},
	{'GR','A'},
	{'RY','LL'},
	{'GG','L'},
	{'GY','BB'},
	{'bR','ALLL'},
	{'gy','AAL'}
};
String[] gameState = {
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'      ',
	'    R ',
	' R  YR',
	'RR  RB'
};

PuzzleFighter.play(instructions)
             .equals( String.join("\n", gameState) );     // -> true

/* STEP-BY-STEP MOVES SEQUENCE
   (GAME STATE at end of each of the first 5 moves)

 MOVE 1      MOVE 2      MOVE 3      MOVE 4      MOVE 5
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║      ║    ║      ║    ║      ║
║      ║    ║      ║    ║ B    ║    ║ B    ║    ║ B    ║
║B     ║    ║BB    ║    ║BB    ║    ║BB    ║    ║BB  RR║
║R     ║    ║RY    ║    ║RYG   ║    ║RYG YB║    ║RYG YB║
*/
```

<h2 style='color:#f66'>Technical Details</h2>

- Input will always be valid.
- Full Test Suite: `10` fixed tests and `200` random tests
- The maximum number of moves in any given test is `100`
- Use Python 3+ for the Python translation
- For JavaScript, most built-in prototypes are frozen, except `Array` and `Function`

<p>Special thanks goes out to <a href='https://www.codewars.com/users/Blind4Basics' style='color:#9f9;text-decoration:none' target='_blank'>@Blind4Basics</a> for his contributions to this kata</p>


If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
