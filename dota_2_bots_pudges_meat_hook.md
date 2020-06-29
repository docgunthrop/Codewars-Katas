<p>You and three of your friends are amateur <a href='https://en.wikipedia.org/wiki/Dota_2' style="color:#9f9;text-decoration:none"><b>Dota 2</b></a> gamers. After watching <a href='https://en.wikipedia.org/wiki/The_International_(Dota_2)' style="color:#9f9;text-decoration:none"><i>The International</i></a> of 2017 where the winning team won just shy of <a href='https://en.wikipedia.org/wiki/The_International_2017#Winnings' style="color:#9f9;text-decoration:none">$11 million USD</a>, you've decided to enter the professional scene. The problem is that you only have four players and a team requires five, so you'll have to seek one out. In the meantime, you'll practice with a bot of your own design.</p>

<p>Your bot will play the hero <a href='https://dota2.gamepedia.com/Pudge' style="color:#9f9;text-decoration:none">Pudge</a>. In this kata, your goal is to create a constructor function and method that will handle his signature ability, the <a href='https://dota2.gamepedia.com/Pudge#Meat_Hook' style="color:#9f9;text-decoration:none">Meat Hook</a>.</p>

<p>The <b>Meat Hook</b> is a bloody hook that Pudge launches toward a unit or location. The hook will snag the first unit it encounters, dragging the unit back to Pudge and dealing damage if it is an enemy.</p>

<video controls autoplay='autoplay' loop='loop'><source src="https://giant.gfycat.com/DefensiveFarKilldeer.mp4" type='video/mp4'/></video>

```
MEAT HOOK STATS:
(distance measured in unit value "dst")
Speed: 1450 dst/second
Max Distance @ Level:
Level 1: 1100
Level 2: 1200
Level 3: 1300
Level 4: 1400
```

<h2 style='color:#f88'>Input</h2>
<p>The name of your method will be <code>meatHook</code>(JavaScript) or <code>meat_hook</code>(Python). It will receive an object representing an enemy hero which will include the following properties:</p>
<ul>
	<li><span style='color:#8df'><b>speed</b>:</span> enemy's movement speed in <code>dst / second</code></li>
	<li><span style='color:#8df'><b>start</b>:</span> initial position given by <code>x</code> and <code>y</code> <a href='https://en.wikipedia.org/wiki/Cartesian_coordinate_system' style="color:#9f9;text-decoration:none">Cartesian coordinates</a></li>
	<li><span style='color:#8df'><b>end</b>:</span> "estimated" destination given by <code>x</code> and <code>y</code> values</li>
</ul>

<p><b>Note:</b> the property <code>end</code> is stated as "estimated" because it is not to be treated as a line segment ending at <code>end</code>, but as a <a href='https://en.wikipedia.org/wiki/Line_(geometry)#Ray' style="color:#9f9;text-decoration:none">ray</a> with the origin at <code>start</code>. In other words, assume that the enemy's path continues beyond the <code>end</code> point, indefinitely.</p>

<h2 style='color:#f88'>Output</h2>
<p>An array/list of length <code>2</code> comprised of:</p>
<ul>
	<li>contact point (<code>[x,y]</code>) of the hookshot if the enemy can be hooked (rounded to nearest integers)</li>
	<li>hook launch time rounded to the nearest millisecond</li>
</ul>
<p>If the enemy cannot be hooked, return <code>null</code>(JavaScript) or <code>None</code>(Python).</p>

<h2 style='color:#f88'>Technical Details</h2>
<div><img src="https://i.imgur.com/OFaOUjO.png" alt="hook range diagram"></div>
In the above image, the <span style='color:#ff8c00'>orange</span> circle represents Pudge's hook range at level 1 and the <span style='color:#00b4ff'>blue</span> circle represents the hook range at level 4. The ray represents the enemy's path.</br>
At level 1, the enemy is out of range. At level 4, the enemy can be hooked at any point along the green line segment in the shaded sector.

<ul>
	<li>Pudge's <code>[x,y]</code> position is fixed at <code>[0,0]</code></li>
	<li>Your function should hook at the earliest possible point when the enemy unit comes into range</br>
	In the image above, Pudge should hook as close to <span style='color:#ff0'>point A</span> as possible
	</li>
	<li>Enemy's <code>speed</code> will always fall in the range: <code>550 >= speed >= 270</code></li>
	<li>Enemy's <code>start</code> position will always be outside Pudge's hook range</li>
	<li>Enemy's path (with indeterminate destination) will always cross at least <b>one</b> axis</li>
	<li>After every 10 successful hookshots, Pudge levels up; each level-up increases his hook range (refer to <code>MEAT HOOK STATS</code> above)</li>
	<li>Pudge begins at level <code>1</code></li>
	<li>Inputs will always be valid</li>
</ul>

<h2 style='color:#f88'>Test Example</h2>

```javascript
let pudge = new Pudge();
let test = {speed: 325, start: [1800,240], end: [200,-1025]};

pudge.meatHook(test); // [[1039, -362], 2227]
```
```python
pudge = Pudge()
test = {speed: 325, start: [1800,240], end: [200,-1025]}

pudge.meat_hook(test) # [[1039, -362], 2227]
```

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
