<!--Area of House from Path of Mouse-->
<img src='https://i.imgur.com/IVdNZe1.png'/><br/>
<sup style='color:#ccc'><i>Above: An overhead view of the house in one of the tests. The green outline indicates the path taken by K</i></sup>
<p>A mouse named K has found a new home on Ash Tree Lane. K wants to know the size of the interior of the house (which consists of just one room). K is able to measure precise distances in any direction he runs. But K is wary of open spaces and will only run alongside walls, as mice tend to do. In this house the walls always connect at right angles.</p>
<p>K's plan is to run alongside the walls, traversing the entire perimeter of the room, starting and ending at K's mousehole. K memorizes the path as an alternating sequence of distance traveled and directional turn. Your task is to write a function that will find the area of the house interior when given K's path.</p>

<h2 style='color:#f88'>Input</h2>

Your function will receive a string as an argument. The string will consist of turns (`L` or `R`, for `left` and `right`, respectively) and positive integers, in an alternating sequence. `L`/`R` represents the turn direction made by K, and the integers mark the number of distance units to move forward.

<h2 style='color:#f88'>Output</h2>

Your function should return an integer representing the area of the house, based on K's path. If K's path is not a valid path, return `null` or `None`.

<h2 style='color:#f88'>Invalid Paths</h2>

A path is <strong>invalid</strong> if it meets any of the following criteria:
- the path intersects/overlaps itself (with the exception of the mousehole when completing the loop); see examples of path fragments below
- the path doesn't complete the loop back to the mousehole
- the mousehole is located along the straight path of a wall (K's mousehole must be located at a convex/concave corner position to be valid)

<h3 style='color:#95c4ffff'>Invalidating overlap path fragment examples</h3>
<img src='https://i.imgur.com/3oU2dWM.png' style='height:150px'/>
<img src='https://i.imgur.com/SWqM8SR.png' style='height:150px'/>
<img src='https://i.imgur.com/ET1nCER.png' style='height:150px'/>

- Example A: Perpendicular intersection `...5L2L3L4...`
- Example B: Point of overlap `...2L2R3R2R3L2...`
- Example C: Parallel overlap `...4L2R2R3R4R1L2...`


<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/GwEydDN.png'/><br/>
<sup style='color:#ccc'>The circled K and green arrow indicate the starting position and direction as given in the example test below</sup>

```python
mouse_path('4R2L1R5R9R4R4L3') # 49
```

```javascript
mousePath('4R2L1R5R9R4R4L3') // 49
```

<h2 style='color:#f88'>Additional Details</h2>

- K's path will always consist of fewer than `500` turns
- The area of the house (when valid) will always be less than `2**32`
- Full Test Suite: `12` fixed tests and `150` random tests
- Use Python 3+ for the Python translation
- For JavaScript, most built-in prototypes are frozen, except `Array` and `Function`
- All inputs will be of valid type and pattern (that is, it will alternate between distance moved and directional turn)
- NOTE: the random test generator may, on very rare occasions, throw an error (around 0.01% of the time, based on my observation); if you get an error pointing to the random test function, try running your solution again.
- This kata was inspired by [Kafka](https://en.wikipedia.org/wiki/A_Little_Fable) and [Danielewski](https://en.wikipedia.org/wiki/House_of_Leaves)

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
