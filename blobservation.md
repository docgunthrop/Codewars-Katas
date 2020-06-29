<!--Blobservation-->
<p>Blobs of various sizes are situated in a room. Each blob will move toward the nearest smaller blob until it reaches it and engulfs it. After consumption, the larger blob grows in size.</p>
<p>Your task is to create a class <code>Blobservation</code> (a portmanteau of blob and observation) and methods that give information about each blob after an arbitrary number of moves.</p>

<h2 style='color:#f88'>Class Details</h2>
<p>A <code>Blobservation</code> class instance is instantiated with two integer values, <code>h</code> and <code>w</code>, that represent the dimensions of the room. The instance methods are as follows:</p>
<h3 style='color:#8df'>populate</h3>
<p>The <code>populate</code> method is called with an array/list representing a list of blobs.</p>
<ul>
	<li>Each element is an object/dict (<code>Map&lt;String,Integer&gt;</code> in Java) with the following properties:</br>
	<ul>
		<li><code>x</code>: vertical position</li>
		<li><code>y</code>: horizontal position</li>
		<li><code>size</code>: size of the blob</li>
	</ul></li>
	<li>This method may be called multiple times on the same class instance</li>
	<li>If a new blob's position is already occupied by an existing blob, the two fuse into a single blob</li>
	<li>If the list input contains any invalid values, discard it entirely and throw an error (do not update/modify the instance)</li>
</ul>

<h3 style='color:#8df'>move</h3>
<p>The <code>move</code> method may be called with up to one argument — a positive integer representing the number of move iterations (ie. turns) to process. If no argument is given, the integer value defaults to <code>1</code>.</p>

<h3 style='color:#8df'>print_state</h3>
<p>The <code>print_state</code> method is a nullary function that returns an array of the positions and sizes of each blob at the current state (Java: a <code>List&lt;List&lt;Integer&gt;&gt;</code> ), sorted in ascending order by <code>x</code> position, then by <code>y</code>. If there are no blobs, return an empty array.</p>

<h2 style='color:#f88'>Blob Movement Behavior</h2>
<p>With each turn, every blob whose <code>size</code> is larger than the smallest blob <code>size</code> value will move to one of the 8 spaces immediately surrounding it (<a href='https://en.wikipedia.org/wiki/Moore_neighborhood' style='color:#9f9;text-decoration:none'>Moore neighborhood</a>) in the direction of the nearest target blob with a lower relative <code>size</code>.</p>
<ul>
	<li>If a target's coordinates differ on both axes, the predatory blob will move diagonally. Otherwise, it will move in the cardinal direction of its target</li>
	<li>If multiple targets are at the same movement distance, the blob with the largest <code>size</code> is focused</li>
	<li>If there are multiple targets that have both the largest <code>size</code> and shortest movement distance, priority is set in clockwise rotation, starting from the <code>12</code> position</li>
	<li>If two blobs pass each other (e.g. swap positions as a result of their movement), they will not fuse</li>
	<li>Blobs of the smallest size remain stationary</li>
</ul>

<h2 style='color:#f88'>Additional Technical Details</h2>
<ul>
	<li>A blob's initial <code>size</code> will range between <code>1</code> and <code>20</code></li>
	<li>Multiple blobs occupying the same space will automatically fuse into one</li>
	<li>When a blob consumes another blob, or when two blobs fuse, the remaining blob's <code>size</code> becomes the sum of the two</li>
	<li>The 2nd argument for the class constructor is optional; if omitted, the room defaults to a square, where <code>w == h</code>.</li>
	<li>Room dimensions (<code>h</code> and <code>w</code>) will range between <code>8</code> and <code>50</code></li>
	<li>Class instances will always be instantiated with valid arguments</li>
	<li>Methods should throw an error if called with invalid arguments</li>
	<li>Boolean values are not to be regarded as valid integers</li>
	<li>Python translation: Use Python 3 only</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/4Moyo7t.png'>
<p>The image above shows the state at turn 0 (the initial state), turn 1, and turn 2.</p>
<ul>
	<li>At <code>T:0</code>, the orange blob at <code>[4,3]</code> with a size of <code>4</code> has four different targets of equal movement distance — the blobs occupying the green, yellow, and red spaces. The adjacent matching-color spaces are the positions it would initially move to in pursuit of each respective target. Here it targets the size <code>3</code> blob at <code>[7,0]</code>.</li>
	<li>At <code>T:1</code>, the size <code>2</code> blob that was in the yellow space has consumed the size <code>1</code> blob at <code>[6,7]</code> and now has a size of <code>3</code></li>
	<li>At <code>T:2</code>, the size <code>3</code> blob in the green space has consumed the size <code>1</code> blob to become the size <code>4</code> blob at <code>[7,2]</code>. At this point, the two orange blobs will both target the green blob at <code>[4,2]</code> and all size <code>2</code> blobs will remain stationary</li>
</ul>
<p></p>

```javascript
const generation0 = [
	{x:0,y:4,size:3},
	{x:0,y:7,size:5},
	{x:2,y:0,size:2},
	{x:3,y:7,size:2},
	{x:4,y:3,size:4},
	{x:5,y:6,size:2},
	{x:6,y:7,size:1},
	{x:7,y:0,size:3},
	{x:7,y:2,size:1}
];
const blobs = new Blobservation(8);
blobs.populate(generation0);
blobs.move();
blobs.print_state(); //[[0,6,5],[1,5,3],[3,1,2],[4,7,2],[5,2,4],[6,7,3],[7,1,3],[7,2,1]]
blobs.move();
blobs.print_state(); //[[1,5,5],[2,6,3],[4,2,2],[5,6,2],[5,7,3],[6,1,4],[7,2,4]]
blobs.move(1000);
blobs.print_state(); //[[4,3,23]]
```
```python
generation0 = [
	{'x':0,'y':4,'size':3},
	{'x':0,'y':7,'size':5},
	{'x':2,'y':0,'size':2},
	{'x':3,'y':7,'size':2},
	{'x':4,'y':3,'size':4},
	{'x':5,'y':6,'size':2},
	{'x':6,'y':7,'size':1},
	{'x':7,'y':0,'size':3},
	{'x':7,'y':2,'size':1}
]
blobs = new Blobservation(8)
blobs.populate(generation0)
blobs.move()
blobs.print_state() #[[0,6,5],[1,5,3],[3,1,2],[4,7,2],[5,2,4],[6,7,3],[7,1,3],[7,2,1]]
blobs.move()
blobs.print_state() #[[1,5,5],[2,6,3],[4,2,2],[5,6,2],[5,7,3],[6,1,4],[7,2,4]]
blobs.move(1000)
blobs.print_state() #[[4,3,23]]
```
```java
List<Map<String,Integer>> generation0 = Arrays.asList(
new HashMap<String,Integer>() {{ put("x", 0); put("y", 4); put("size", 3); }},
new HashMap<String,Integer>() {{ put("x", 0); put("y", 7); put("size", 5); }},
new HashMap<String,Integer>() {{ put("x", 2); put("y", 0); put("size", 2); }},
new HashMap<String,Integer>() {{ put("x", 3); put("y", 7); put("size", 2); }},
new HashMap<String,Integer>() {{ put("x", 4); put("y", 3); put("size", 4); }},
new HashMap<String,Integer>() {{ put("x", 5); put("y", 6); put("size", 2); }},
new HashMap<String,Integer>() {{ put("x", 6); put("y", 7); put("size", 1); }},
new HashMap<String,Integer>() {{ put("x", 7); put("y", 0); put("size", 3); }},
new HashMap<String,Integer>() {{ put("x", 7); put("y", 2); put("size", 1); }}
);

Blobservation blobs = new Blobservation(8);
blobs.populate(generation0);

blobs.move();
blobs.printState(); // [[0,6,5],[1,5,3],[3,1,2],[4,7,2],[5,2,4],[6,7,3],[7,1,3],[7,2,1]]
blobs.move();
blobs.printState(); // [[1,5,5],[2,6,3],[4,2,2],[5,6,2],[5,7,3],[6,1,4],[7,2,4]]
blobs.move(1000);
blobs.printState(); // [[4,3,23]]
```

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
