In traditional [American checkers](https://en.wikipedia.org/wiki/Draughts) (also known as *draughts* outside the U.S.), when one of your pieces becomes a king, it gains the advantage of being able to move diagonally in any direction. This adds more possibilities with regard to capturing multiple enemy pieces in a single turn.

In this kata you are presented with an `n x n` board. While your opponent has several pieces on the board, you have only one remaining piece — a king. Using the same mechanics as in American checkers, your goal is to capture the maximum number of enemy pieces in the next move with your king.

<h2 style='color:#f66'>Input</h2>
<p>Your function will receive an array of length <code>n</code> comprised of strings of length <code>n</code>. Each string value represents each row of the board, from top to bottom.</p>
Each string will consist of one or more of the following:

- `" "`: an unoccupied cell denoted by a space character
- `X`: a cell occupied by an enemy piece
- `K`: the location of your king piece

<h2 style='color:#f66'>Output</h2>
Your function should return the maximum number of enemy pieces that can be captured in one turn.

<h2 style='color:#f66'>Test Example</h2>

```javascript
let board = [
	'       X',
	'        ',
	' X X X  ',
	'        ',
	' X X X  ',
	'        ',
	'   X X  ',
	'    K   '
];
kingMoveCombo(board); //7
```
```python
board = [
	'       X',
	'        ',
	' X X X  ',
	'        ',
	' X X X  ',
	'        ',
	'   X X  ',
	'    K   '
]
king_move_combo(board) #7
```

<p>Below (left) is a graphic representation of the example <code>board</code> and (right) a set of moves to obtain the solution.</p>

![Checkerboard image at https://i.imgur.com/KAs4tIZ.png](https://i.imgur.com/KAs4tIZ.png)

<h2 style='color:#f66'>Technical Details</h2>

- Input will always be valid.
- Board size range: `16 >= n >= 8`
- In JavaScript, prototypes have been frozen and `require` has been disabled.

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
