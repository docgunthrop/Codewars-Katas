<!--Dots and Boxes Validator-->
<p><span style='color:#8df'><a href='https://en.wikipedia.org/wiki/Dots_and_Boxes' style='color:#9f9;text-decoration:none'>Dots and Boxes</a></span> is a game typically played by two players. It starts with an empty square grid of equally-spaced dots. Two players take turns adding a single horizontal or vertical line between two unjoined adjacent dots. A player who completes the fourth side of a <code>1 x 1</code> box earns one point and takes another turn. The game ends when no more lines can be placed.</p>

<p>Your task is to return the scores of the two players of a finished game.</p>

<h2 style='color:#f88'>Input</h2>

Your function will receive an array/tuple of integer pairs, each representing a link between two dots. Dots are denoted by a sequence of integers that increases left to right and top to bottom, like shown below.

```
for a 3 x 3 square

0  1  2

3  4  5

6  7  8
```

<h2 style='color:#f88'>Output</h2>

Your function should return an array/tuple consisting of two non-negative integers representing the scores of both players.

<h2 style='color:#f88'>Test Example</h2>
<img src='https://i.imgur.com/kwS3rDy.png'/><br/>
<!-- <sup style='color:#ccc'>Sequence for the test example</sup> -->

```python
moves = ((0,1),(7,8),(1,2),(6,7),(0,3),(8,5),(3,4),(4,1),(4,5),(2,5),(7,4),(3,6))
dots_and_boxes(moves) # should return (3,1)
```
```javascript
let moves = [[0,1],[7,8],[1,2],[6,7],[0,3],[8,5],[3,4],[4,1],[4,5],[2,5],[7,4],[3,6]];
dotsAndBoxes(moves) // should return [3,1]
```
```go
var moves = [][2]int{{0,1},{7,8},{1,2},{6,7},{0,3},{8,5},{3,4},{4,1},{4,5},{2,5},{7,4},{3,6}}
DotsAndBoxes(moves) // should return [3 1]
```
```haskell
moves = [(0,1),(7,8),(1,2),(6,7),(0,3),(8,5),(3,4),(4,1),(4,5),(2,5),(7,4),(3,6)]
dotsAndBoxes moves -- should return (3,1)
```
```elixir
moves = [{0,1},{7,8},{1,2},{6,7},{0,3},{8,5},{3,4},{4,1},{4,5},{2,5},{7,4},{3,6}]
DnB.dots_and_boxes(moves) # should return {3,1}
```
```csharp
var moves = new int[][]{new[]{0,1}, new[]{7,8}, new[]{1,2}, new[]{6,7}, new[]{0,3} ,new[]{8,5}, new[]{3,4}, new[]{4,1}, new[]{4,5}, new[]{2,5}, new[]{7,4}, new[]{3,6}};
DnB.DotsAndBoxes(moves) // should return int[2]{3,1}
```

<h2 style='color:#f88'>Additional Details</h2>

- All inputs will be valid
- `n x n` board size range: `3 <= n <= 12`
- Full Test Suite: `10` fixed tests and `100` random tests
- Use Python 3+ for the Python translation
- For JavaScript, `module` and `require` are disabled

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
