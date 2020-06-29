<!--Amidakuji-->
<p><span style='color:#8df'><a href='https://en.wikipedia.org/wiki/Ghost_Leg' style='color:#9f9;text-decoration:none'>Amidakuji</a></span> is a method of lottery designed to create random pairings between two sets comprised of an equal number of elements.</p>
<p>Your task is to write a function <code>amidakuji</code> that returns the final positions of each element. Note that the elements are an ascending sequence of consecutive integers starting with <code>0</code> (from left to right).</p>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive an array/list of equal-length strings consisting of <code>0</code> and <code>1</code> characters; this represents the "ladder" structure. The <code>1</code>s represent the rungs of the ladder and the <code>0</code>s represent empty space.<br/><br/>
Each element begins at the top of its corresponding vertical rail, as illustrated in the diagram below.<br/>During the descent of the ladder, whenever a vertical rail intersects a horizontal rung, it swaps values with the adjacent connecting vertical rail.</p>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return an array of integers, with each integer in its final position.</p>

<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/6pJ87vP.png'>
<p>The diagram above is a visual representation of the test example below. The yellow highlighted path shows the path taken by the <code>2</code> value. Each time it encounters a crosspiece, it shifts position.</p>

```javascript
let ladder = [
	'001001',
	'010000',
	'100100',
	'001000',
	'100101',
	'010010',
	'101001',
	'010100'
];

amidakuji(ladder); // [4, 2, 0, 5, 3, 6, 1]
```
```python
ladder = [
	'001001',
	'010000',
	'100100',
	'001000',
	'100101',
	'010010',
	'101001',
	'010100'
]

amidakuji(ladder) # [4, 2, 0, 5, 3, 6, 1]
```
```elixir
ladder = [
	"001001",
	"010000",
	"100100",
	"001000",
	"100101",
	"010010",
	"101001",
	"010100"
]

Banzai.amidakuji(ladder) # [4, 2, 0, 5, 3, 6, 1]
```
```go
ladder := []string{
	"001001",
	"010000",
	"100100",
	"001000",
	"100101",
	"010010",
	"101001",
	"010100",
}

Amidakuji(ladder) // [4 2 0 5 3 6 1]
```
```csharp
var ladder = new string[]{
	"001001",
	"010000",
	"100100",
	"001000",
	"100101",
	"010010",
	"101001",
	"010100"
};

Banzai.Amidakuji(ladder) == new int[]{4,2,0,5,3,6,1}; // true
```

<h2 style='color:#f88'>Other Technical Details</h2>
<ul>
	<li>A function <code>visualizer</code> is preloaded to help illustrate the structure of the ladder; you can call this function with test inputs</li>
	<li>No two rungs will ever be adjacent (so there is no ambiguity about directional path)</li>
	<li>Full Test Suite: <code>10</code> fixed tests and <code>100</code> randomly-generated tests</li>
	<li>Test input dimension upper bounds:<br/>
		<ul>
			<li>maximum width: <code>20</code></li>
			<li>maximum height: <code>50</code></li>
		</ul>
	</li>
	<li>Inputs will always be valid</li>
</ul>

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
