<p>Spider-Man ("Spidey") needs to get across town for a date with Mary Jane and his web-shooter is low on web fluid. He travels by slinging his web rope to latch onto a building rooftop, allowing him to swing to the opposite end of the latch point.</p>
<p>Write a function that, when given a list of buildings, returns a list of optimal rooftop latch points for minimal web expenditure.</p>

<h2 style='color:#f88'>Input</h2>
<p>Your function will receive an array whose elements are subarrays in the form <code>[h,w]</code> where <code>h</code> and <code>w</code> represent the height and width, respectively, of each building in sequence</p>

<h2 style='color:#f88'>Output</h2>
<p>An array of latch points (integers) to get from <code>0</code> to the end of the last building in the input list</p>

<h2 style='color:#f88'>Technical Details</h2>
<ul>
	<li>An optimal latch point is one that yields the greatest horizontal distance gain relative to length of web rope used. Specifically, the highest horizontal distance yield per length unit of web rope used. Give this value rounded down to the nearest integer as a distance from Spidey's origin point (<code>0</code>)</li>
	<li>At the start of each swing, Spidey selects a latch point based on his current position.</li>
	<li>At the end of each swing, Spidey ends up on the opposite side of the latch point equal to his distance from the latch point before swing.</li>
	<li>Spidey's initial altitude is <code>50</code>, and will always be the same at the start and end of each swing. His initial horizontal position is <code>0</code>.</li>
	<li>To avoid collision with people/traffic below, Spidey must maintain a minimum altitude of <code>20</code> at all times.</li>
	<li>Building height (<code>h</code>) range limits: <code>125 &lt;= h &lt; 250</code></li>
	<li>Building width (<code>w</code>) range limits: <code>50 &lt;= w &lt;= 100</code></li>
	<li>Inputs will always be valid.</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>

![test example image](https://i.imgur.com/Z2hAWPn.png)
- Spidey's initial position is at `0`, marked by the Spidey icon on the left. His first latch point is marked by the green circle at `76` (horizontal position) on `buildings[0]`.
- At the end of the swing, Spidey's position is at the point marked `B` with a horizontal position of `152`. The green arc represents Spidey's path during swing.
- The orange circle on the 3rd building and the orange arc going from point `B` to point `C` represent the latch point (`258`) and arc path for the next swing.

```javascript
let buildings = [[162,76], [205,96], [244,86], [212,68], [174,57], [180,89], [208,70], [214,82], [181,69], [203,67]];

spideySwings(buildings); //[76,258,457,643,748]
```
```python
buildings = [[162,76], [205,96], [244,86], [212,68], [174,57], [180,89], [208,70], [214,82], [181,69], [203,67]]

spidey_swings(buildings)# [76,258,457,643,748]
```

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
