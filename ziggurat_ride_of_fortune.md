<p>You and a group of explorers have found a legendary ziggurat hidden in an obscure jungle. According to legend, the ancient structure houses portals to other worlds.</p>
<p>The outer west wall of the ziggurat consists of a series of entrance doors. When an explorer enters through a door, they sit in a mobile cart that moves in a straight path until it reaches a "switch" or hits a wall.</p>
<p>A <span style="color:#8df">switch</span> re-routes the cart either left or right, depending on the state of the switch and the cart's movement direction.</p>
<p>Interdimensional portals line the entire north, east, and south walls inside the ziggurat. If a cart hits one of these walls, the occupying explorer exits through the portal before them. If a cart ends at the west wall, the explorer exits through a door and returns back outside.</p>
<p>The expedition leader has assigned to you the task of keeping track of the exit points of each explorer. You are given an artifact that provides you with a map of the ziggurat's inner chamber.</p>

<h2 style='color:#f88'>Switch Mechanics</h2>
<div style="width:310px;height:260px;background:#000;padding:5px"><img src="https://i.imgur.com/RHPCVqC.png"></div>
<p>Above is a representation of a switch. It exists in one of two states <code>A</code> or <code>B</code>.</p>
<ul>
	<li>If a switch is in the <code>A</code> state and and a cart enters by moving:
		<ul>
			<li><b>west</b>, they are routed north</li>
			<li><b>east</b>, they are routed south</li>
			<li><b>south</b>, they are routed east</li>
			<li><b>north</b>, they are routed west</li>
		</ul></li>
	<li>If the switch were in the <code>B</code> state, the cart would be routed in the orthogonal direction opposite to that for the <code>A</code> state.</li>
	<li>Immediately after a cart passes through a switch, the switch changes state by rotating 90 degrees.</li>
</ul>

<h2 style='color:#f88'>Cart Pathing</h2>
<img src="https://i.imgur.com/UChfJkG.png">
<p>Above left is an example ziggurat with four switches in their initial states. The <code>S</code> in the green arrow represents the initial position of the explorer who enters the structure through door <code>1</code>.<br/>
The switches at <code>[1,1]</code>, <code>[1,4]</code>, and <code>[4,1]</code> begin in state <code>A</code>, while the switch at <code>[4,4]</code> begins in state <code>B</code>.</p>
<ul>
	<li>The left image shows the path followed by the cart (in sequence, denoted by the white dashed arrows labeled <code>1</code>, <code>2</code>, and <code>3</code>). First it travels through the switch at <code>[1,1]</code>, then <code>[4,1]</code>, and then <code>[4,4]</code>.</li>
	<li>The right image shows the remainder of the cart's path, up to the explorer's exit (marked by the red arrow).<br/>By step <code>4</code> (after exiting the switch at <code>[1,4]</code>), the state of all four switches have changed, as shown above.</li>
	<li>The end state for the switch at <code>[1,4]</code> is <code>B</code>, while the rest end in state <code>A</code>.</li>
	<li>If the next explorer in sequence were also to enter through door <code>1</code>, they would exit through the portal at <code>[5,4]</code>.</li>
</ul>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive two arguments:</p>
<ul>
	<li>An <code>n</code> x <code>n</code> matrix representing the layout of the ziggurat interior.</li>
	<li>An array/list of the doors (rows) entered by each explorer in sequence. Assume each following explorer enters immediately after the preceding explorer has exited.</li>
</ul>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return an array of the exit points of explorers who exit through portals and <code>null</code>/<code>None</code> for those who return back outside.</p>

<h2 style='color:#f88'>Test Example</h2>

```javascript
let artifact = [
	'      ',
	' A  A ',
	'      ',
	'      ',
	' A  B ',
	'      '];
let explorers = [1,1,0,3,4,4,2,5,1,4];
rideOfFortune(artifact,explorers); //[null,[5,4],[0,5],[3,5],[0,4],[5,1],[2,5],[5,5],null,[5,1]]
```
```python
artifact = [
	'      ',
	' A  A ',
	'      ',
	'      ',
	' A  B ',
	'      ']
explorers = [1,1,0,3,4,4,2,5,1,4]
ride_of_fortune(artifact,explorers) #[None,[5,4],[0,5],[3,5],[0,4],[5,1],[2,5],[5,5],None,[5,1]]
```
```go
artifact := []string{
	"      ",
	" A  A ",
	"      ",
	"      ",
	" A  B ",
	"      ",
}
explorers := []int{1,1,0,3,4,4,2,5,1,4}
RideOfFortune(artifact,explorers) // [[-1 -1] [5 4] [0 5] [3 5] [0 4] [5 1] [2 5] [5 5] [-1 -1] [5 1]]
```
```csharp
string[] artifact = {
	"      ",
	" A  A ",
	"      ",
	"      ",
	" A  B ",
	"      "
};
int[] explorers = {1,1,0,3,4,4,2,5,1,4};
Ziggurat.RideOfFortune(artifact,explorers); // {{-1,-1}, {5,4}, {0,5}, {3,5}, {0,}] ,{5,1}, {2,5}, {5,5}, {-1,-1}, {5,1}}
```
```java
String[] artifact = { " ",
" A A ",
" ",
" ",
" A B ",
" "};
int[] explorers = {1,1,0,3,4,4,2,5,1,4};
List<Point> sol = Ziggurat.ride_of_fortune(artifact,explorers) // [null,(5,4),(0,5),(3,5),(0,4),(5,1),(2,5),(5,5),null,(5,1)]
```

<h2 style='color:#f88'>Technical Constraints</h2>

- Ziggurat size `n` range: `40 >= n >= 6`
- Final Test Suite: `15` fixed tests, `100` random tests
- JavaScript: prototypes have been frozen and `require` has been disabled
- Inputs will always be valid

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
