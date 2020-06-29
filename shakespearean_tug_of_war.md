<blockquote style="max-width:360px;min-width:200px;border-color:#777;background-color:#111;font-family:Georgia,Verdana,serif"><strong>&ldquo;Do you bite your thumb at us, sir?&rdquo;</strong><br/><p style="text-align:right;font-family:serif"><i>Romeo and Juliet</i> Act I: Sc. 1</p></blockquote>

<p>Prince Escalus and the citizens of Verona have become weary of the ongoing blood-feud between the Montagues and the Capulets. Escalus has decided to settle the feud once and for all with a game of <a href='https://en.wikipedia.org/wiki/Tug_of_war' style="color:#9f9;text-decoration:none">tug of war</a> between the two houses, resulting in the losing family leaving the city.</p>

<h2 style='color:#f88'>Objective</h2>
<p>This version of tug of war will begin with one member from each house on opposite sides of the center line. Gradually over time, additional members from each house will join their respective side until a winner has been declared or there are no more additional participants.</br>
A house wins if the opposing house touches the center point.</p>

<p>Your goal is to write a function that returns the winner between the two houses and the elapsed time when victory is declared.</p>

<h2 style='color:#f88'>Input</h2>
The function will accept two arguments:
<ul>
	<li>An integer distance <code>n</code> between the two closest members of opposite families (see test example below)</li>
	<li>An array/list of subarrays. Each subarray will contain three integer values:
		<ul>
			<li>The pulling force of the participant from House Capulet</li>
			<li>The pulling force of the participant from House Montague</li>
			<li>The number of seconds since the last participants had joined the tug of war</li>
		</ul>
	</li>
</ul>
<p>Inputs will always be valid.</p>

<h2 style='color:#f88'>Output</h2>
An array with two elements:
<ul>
	<li>The winning house: either <code>Montague</code> or <code>Capulet</code> (string)</li>
	<li>The elapsed time in seconds (integer)</li>
</ul>
<p>If the tug of war results in a deadlock, return <code>null</code> or <code>None</code>.</p>

<p><span style="color:#f88"><b>Rope Movement</b></span></br>
When the aggregate pulling force on one side is equal to that of the other, there is no rope movement. If this is the state after all house members have joined the tug of war, the result is a deadlock.</p>
<p>If one side has a greater aggregate pulling force, the rope moves at a rate of <code>n * decimeters/second</code> where <code>n</code> is the difference in total pulling force between the Capulets and Montagues currently engaaged in the tug of war.</p>

<h2 style='color:#f88'>Test Example</h2>
<div style='background:#000;display:flex;flex-direction:column;justify-content:space-between;width:370px;height:260px;padding:5px'><img src="https://i.imgur.com/sjRqcqJ.png" alt="status at 0 seconds"></br><img src="https://i.imgur.com/Ol6B3ze.png" alt="status at 8 seconds"></div>
<p style='font-size:0.9em'>The first image above represents the status at <code>0</code> seconds (<code>members[0]</code>).</br>
The image below it represents the status at <code>8</code> seconds (<code>members[1]</code>).</p>

<ul>
	<li>In the above images, the solid green triangle marks the <span style='color:#00dc00'><b>center point</b></span>.</li>
	<li>At <code>0</code> seconds, a member from each side joins.</br>
	<code>8</code> seconds later, the line will have moved <code>2.4</code> meters to the left. Another member from each house joins behind their respective preceding member.</li>
</ul>

```javascript
let members = [[35,32,0],[38,46,8],[27,24,12],[30,28,22],[39,36,31],[32,40,12],[28,18,6],[47,50,16]];

tugOfWar(20,members); //['Capulet', 154]
```
```python
members = [[35,32,0],[38,46,8],[27,24,12],[30,28,22],[39,36,31],[32,40,12],[28,18,6],[47,50,16]]

tug_of_war(20,members) #['Capulet', 154]
```

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
