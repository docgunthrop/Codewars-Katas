<!--Four Pass Transport-->
<p>The eccentric candy-maker, Billy Bonka, is building a new candy factory to produce his new 4-flavor sugar pops. The candy is made by placing a piece of candy base onto a conveyer belt which transports the candy through four separate processing stations in sequential order. Each station adds another layer of flavor.</p>
<p>Due to an error in the factory blueprints, the four stations have been constructed in incorrect locations. It's too costly to disassemble the stations, so you've been called in.</p>
<p>Arrange the directional path of the conveyer belt so that it passes through each of the stations in sequential order while also traveling the shortest distance possible.</p>

<h2 style='color:#f88'>Input</h2>
<p>An array consisting of the locations of each station on the factory floor, in order. The factory floor is a <code>10</code> x <code>10</code> matrix (with <code>0</code> starting index).</p>

<h2 style='color:#f88'>Output</h2>
<p>Your function should return the path of the conveyer belt as an array.</br>
If a valid configuration is not possible, return <code>null</code> or <code>None</code>.</p>

<p>The position values in the input and output arrays will consist of integers in the range <code>0 - 99</code>, inclusive. These integers represent a position on the factory floor.</br>
For example, the position <code>[0,8]</code> is given as <code>8</code>, and <code>[4,6]</code> is given as <code>46</code></p>

<h2 style='color:#f88'>Technical Details</h2>
<ul>
	<li>The conveyer belt must run through each station once and in ascending order</li>
	<li>The conveyer belt  must not intersect/overlap itself</li>
	<li>The distance covered by the conveyer belt must be the minimum necessary to complete the task</li>
	<li>Full Test Suite: <code>30</code> fixed tests, <code>100</code> random tests (2000 in java)</li>
	<li>Inputs will always be valid and each test will have zero or more possible solutions..</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>
<img src="https://i.imgur.com/eAofgDs.png" alt="4 stations">

```javascript
//INPUT - reference image A
let stations = [0,65,93,36];
fourPass(stations);

//OUTPUT #1 - reference image B
// [0, 1, 2, 3, 4, 5, 15, 25, 35, 45, 55, 65, 64, 63, 73, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]

//OUTPUT #2 - reference image C
// [0, 10, 20, 30, 40, 50, 60, 61, 62, 63, 64, 65, 75, 85, 84, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]
```
```python
# INPUT - reference image A
stations = [0,65,93,36]
four_pass(stations)

# OUTPUT #1 - reference image B
# [0, 1, 2, 3, 4, 5, 15, 25, 35, 45, 55, 65, 64, 63, 73, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]

# OUTPUT #2 - reference image C
# [0, 10, 20, 30, 40, 50, 60, 61, 62, 63, 64, 65, 75, 85, 84, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]
```
```java
// INPUT - reference image A
int[] stations = {0,65,93,36};
new FPT(stations).solve();

// OUTPUT #1 - reference image B
// [0, 1, 2, 3, 4, 5, 15, 25, 35, 45, 55, 65, 64, 63, 73, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]

// OUTPUT #2 - reference image C
// [0, 10, 20, 30, 40, 50, 60, 61, 62, 63, 64, 65, 75, 85, 84, 83, 93, 94, 95, 96, 86, 76, 66, 56, 46, 36]
```

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
