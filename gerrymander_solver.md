<!--Gerrymander Solver-->
<img src="https://i.imgur.com/8UQHI9E.jpg">
<p><span style='color:#8df'><b><a href='https://en.wikipedia.org/wiki/Gerrymandering' style='color:#9f9;text-decoration:none'>gerrymander</a></b></span> — <i>noun.</i> the dividing of a state, county, etc., into election districts so as to give one political party a majority in many districts while concentrating the voting strength of the other party into as few districts as possible.</p>

<h2 style='color:#f88'>Objective</h2>
<p>Given a <code>5 x 5</code> region populated by <code>25</code> citizens, your task is to write a function that divides the region into <code>5</code> districts given the following conditions:</p>
<ul>
	<li><code>10</code> citizens will vote for your candidate, while the other <code>15</code> will vote for the opponent</li>
	<li>Your candidate must win the popular vote for <code>3</code> of the <code>5</code> districts</li>
	<li>Each district must have an equal number of voters</li>
	<li>Each district must be one contiguous cluster of voters (i.e. each voter has one or more orthogonally adjacent neighbors from the same district)</li>
</ul>

<h2 style='color:#f88'>Concept Overview</h2>
<img src='https://i.imgur.com/FxmmO8y.png'>
<p><code>A</code>: You're given a <code>5 x 5</code> square matrix representing the layout of the region occupied by eligible voters. The following panels show different ways to set boundaries for <code>5</code> districts.</p>
<ul>
	<li><code>B</code>: Proportionate outcome — blue and red win in proportion to their voting</li>
	<li><code>C</code>: Disproportionate outcome — blue wins all</li>
	<li><code>D</code>: <span style='background:#600'>Disproportionate outcome — red wins majority despite having fewer total supporters</span></li>
</ul>
<p>Your function must solve the challenge presented in panel <code>D</code></p>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive a newline-separated string consisting of <code>X</code> and <code>O</code> characters. The <code>O</code>s represent the voters in support of your candidate, and the <code>X</code>s represent those in support of the opponent.</p>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return a <code>5x5</code> newline-separated string comprised of the digits <code>1</code> through <code>5</code> where each group of identical digits represents its own unique district.</p>
<p>If a solution does not exist, return <code>null</code>, <code>None</code>, or <code>nil</code></p>

<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/EFzVwB7.png'>

```javascript
let region = [
	'OOXXX',
	'OOXXX',
	'OOXXX',
	'OOXXX',
	'OOXXX'
].join('\n');

// one possible solution where regions 1,2, and 3 are won
gerrymander(region); // '11114\n12244\n22244\n35555\n33335'
```
```python
region = [
	'OOXXX',
	'OOXXX',
	'OOXXX',
	'OOXXX',
	'OOXXX'
]

# one possible solution where regions 1,2, and 3 are won
gerrymander('\n'.join(region)) # '11114\n12244\n22244\n35555\n33335'
```
```java
String region = String.join("\n",
	"OOXXX",
	"OOXXX",
	"OOXXX",
	"OOXXX",
	"OOXXX"
);

// one possible solution where regions 1,2, and 3 are won
gerrymander(region);
// "11114\n12244\n22244\n35555\n33335"
```

<h2 style='color:#f88'>Testing Constraints</h2>

~~~if:javascript
- Full Test Suite: `10` fixed tests and `50` randomly-generated tests
~~~
~~~if:python
- Full Test Suite: `10` fixed tests and `10` randomly-generated tests
~~~
~~~if:java
- Full Test Suite: `15` fixed tests and `100` randomly-generated tests
~~~
~~~if:cpp
- Full Test Suite: `10` fixed tests and `100` randomly-generated tests
~~~
~~~if:ruby
- Full Test Suite: `10` fixed tests and `10` randomly-generated tests
~~~
- Zero or more valid solutions will exist for each test
- Inputs will always be valid

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
