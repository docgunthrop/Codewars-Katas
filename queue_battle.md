<!--Queue Battle-->

<blockquote style="max-width:400px;min-width:200px;border-color:#777;background-color:#111;font-family:Tahoma,Verdana,serif"><strong>&ldquo;"Forward!", he cried from the rear<br/>
And the front rank died<br/>
The general sat and the lines on the map<br/>
Moved from side to side&rdquo;</strong><br/><p style="text-align:right;font-family:serif"><i>Us and Them</i> -- Pink Floyd</p></blockquote>

<p>A few army battalions from warring nations have met on an even battlefield. Each nation has one battalion present and all battalions have an equal number of soldiers. Every soldier is armed with one rifle and unlimited ammunition. Every soldier also has perfect shooting accuracy. And all armies follow the rules of engagement below.</p>

<h2 style='color:#f88'>Rules of Engagement</h2>
<p><b>1.</b> Each army battalion forms its own straight line queue<br/>
<b>2.</b> Each line is formed such that the head of each queue faces the head of the opposing army queue to its left (or when there are only two remaining armies, both queues face toward each other)<br/>
<b>3.</b> All queue heads maintain equal distance from their respective targets<br/>
<span style='color:#0c0'><b>4.</b></span> There is a <code>1</code> second delay for each queue head to fire his weapon (time taken to lift weapon, aim, then fire)<br/>
<span style='color:#0c0'><b>5.</b></span> If a queue head gets hit by any bullets during that 1 second delay (including at the exact moment the head is expected to shoot), he falls before he can fire his rifle. Otherwise, he shoots his rifle and immediately walks back to the end of his queue.<br/>
<span style='color:#8df;'>Note that the head will receive all bullets that reach his position during that round.</span><br/>
<span style='color:#0c0'><b>6.</b></span> The next soldier in queue then takes his place as head at the start of the next round. If there is only one soldier remaining in a queue, he will stand in place and shoot his rifle every round until he falls or emerges victorious<br/>
<b>7.</b> An army is eliminated when all its soldiers have fallen. When an elimination occurs, the eliminator changes their target to the next army queue in sequence at the start of the next round.<br/>
<span style='color:#d84'>
<b>8.A.</b></span> If an elimination occurs during the round, then all remaining armies reposition themselves at the start of the next round and repeat the cycle from step <code>2</code>. <span style='color:#8df;'>All bullets still in flight at the end of the round will miss all their targets when the repositioning occurs.</span><br/>
<span style='color:#d84'>
<b>8.B</b></span> If no elimination occurs in the round, start again from step <code>4</code>.<br/><br/>

The Rules of Engagement are followed until there are <code>0</code> or <code>1</code> surviving armies.<br/>
Each round (i.e. queue shift) has a one second duration and the heads of each queue shoot at the same time<br/>

<h2 style='color:#f88'>Weapons</h2>

All nations purchase their munitions from the same supplier, Discount Rifles and Bullets, Inc. (aka DRABI)<br/>
All DRABI rifles have perfect firing accuracy. However, because many different machines are used to manufacture the rifles, rifles may have different bullet speeds.

You have a master list of bullet speeds for each rifle and you also know the initial arrangement of all queues in battle. With those resources, you seek to find out which, if any, army survives.


<h2 style='color:#f88'>Input</h2>

Your function will receive anywhere from `3` to `9` arguments:
- The first argument will always be positive integer representing the `distance` between each queue head and his target
- Any additional arguments will each be given as an array/tuple of positive integers; these arrays each represent an army battalion. Each `i`th value in a given array represents the bullet speed for the `i`th soldier's rifle in that battalion's queue.


<h2 style='color:#f88'>Output</h2>
<p>Return the number of the surviving army, given as its argument position.
Also return an array/tuple of that army's surviving soldiers, by index position from its original list. This list should be sorted in queue order, starting with the queue head at time of victory.<br/>
If all battalions are wiped out and there are no survivors, return <code>-1</code> and an empty array/tuple.</p>


<h2 style='color:#f88'>Test Example</h2>

<img src='https://i.imgur.com/RFWZ83d.png'>

The image above references the example given below.
In our example, we are given `3` armies that form their respective queues. Each head (green pointed indicators) faces and fires at the opponent head to the left.
In the tests, each queue head shoots at the head of the next queue that follows, and completes the loop with the last queue shooting at the first.

The image below represents the queues after army `C` is eliminated. Note they change formation and face each other while always maintaining the same distance.

<img src='https://i.imgur.com/pVClMJl.png'>

```go
// in Go the first argument is given as a uint32 value
// subsequent arguments are given as arrays of uint32 values
var A = []uint32{98,112,121,95,63}
var B = []uint32{120,94,90,88,30}
var C = []uint32{116,144,45,200,32}

// the function should return two values: an int and an array of uint32 values
// In our example, the first army emerges as the sole survivor, and the remaining queue for that army consists of only the 3rd soldier
QueueBattle(300,A,B,C) // returns 0,[]uint32{2}
```
```python
# in Python the first argument is given as a positive int
# subsequent arguments are given as tuples of positive ints
A = (98,112,121,95,63)
B = (120,94,90,88,30)
C = (116,144,45,200,32)

# the function should return a tuple of two elements: an integer and a tuple of integers
# In our example, the first army emerges as the sole survivor, and the remaining queue for that army consists of only the 3rd soldier
queue_battle(300,A,B,C) # returns the tuple (0,(2,))
```
```javascript
// in JavaScript the first argument is given as a positive integer
// subsequent arguments are given as arrays of positive integers
const A = [98,112,121,95,63];
const B = [120,94,90,88,30];
const C = [116,144,45,200,32];

// the function should return an array of two elements: an integer and an array of integers
// In our example, the first army emerges as the sole survivor, and the remaining queue for that army consists of only the 3rd soldier
queueBattle(300,A,B,C); // returns the array [0,[2]]
```

<p>In our example, we saw the new positioning when going from <code>3</code> to <code>2</code> queues. Other tests will have a random number of queues (up to a max of <code>8</code>).<br/>
The following diagrams serve as a visual guide to show other battle positions formed depending on the number of active queues.</p>

<img src='https://i.imgur.com/qk791nn.png'>
<img src='https://i.imgur.com/XuMmBzt.png'>

<h2 style='color:#f88'>Technical Details</h2>

- All tests will be valid
- Test constraints:
	- `2 <= number of queues <= 8`
	- `8 <= bullet speed < 2e6`
	- `80 <= distance < 1e6`
	- `bullet speed >= distance/10`
	- `5 <= queue length < 2000`
- Use Python 3.6+ for the Python translation
- In JavaScript, `module` and `require` are disabled
- Full Test Suite: `10` fixed tests and `150` random tests


<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
