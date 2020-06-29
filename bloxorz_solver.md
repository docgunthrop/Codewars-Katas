<video controls autoplay='autoplay' loop='loop'><source src="https://thumbs.gfycat.com/PaleQuestionableGoldeneye-mobile.mp4" type='video/mp4'/></video>

<sub><b>Above:</b> <a href="https://thumbs.gfycat.com/PaleQuestionableGoldeneye-mobile.mp4">Game footage from Bloxorz online game</a></sub>

This kata is inspired by [**Bloxorz**](http://miniclip.wikia.com/wiki/Bloxorz), a flash-based 3D puzzle game where the objective is to maneuver a block to have it fall through a square hole.

# Objective
Your goal is to maneuver a [rectangular cuboid](https://en.wikipedia.org/wiki/Cuboid) with dimensions `1 x 1 x 2` on a 2-dimensional grid made up of `1 x 1` square tiles. While moving the cuboid around, your block must never, at any point, have any part of its bottom-facing surface exposed to open air.

## Input
Your function will receive an array of strings describing the layout of the grid to be traversed. A `1` represents solid ground (tiles), a `0` represents open air, a `B` represents your starting position, and an `X` represents the square hole (destination).

## Output
Your function must return a string representing the minimum sequence of moves required to get the block into the square hole. It will consist of a combination of the following characters: `U` (up), `D` (down), `L` (left), `R` (right).

## Block Movement
![](https://i.imgur.com/6k4Oufb.png)

The block can cover either one or two tiles with each movement, depending on whether it is standing upright or on its long end. The image above shows an overhead view; the yellow squares represent the tiles occupied by the block and the green squares represent the tiles occupied when moved toward a given cardinal direction.

In Fig. 1, the block's position is standing upright, and in Fig. 2, the block is on its long end.

## Test Example
```javascript
let level1 = ['1110000000',
			  '1B11110000',
			  '1111111110',
			  '0111111111',
			  '0000011X11',
			  '0000001110'];

bloxSolver(level1); //'RRDRRRD' or 'RDDRRDR'
```
```python
level1 = [
	'1110000000',
	'1B11110000',
	'1111111110',
	'0111111111',
	'0000011X11',
	'0000001110'
]

blox_solver(level1) #'RRDRRRD' or 'RDDRRDR'
```
An overhead view of the game grid for the example `level1` is shown below, with a green square representing the starting position of the block, the red square representing the square hole, the light grey squares representing the platform tiles, and the dark grey areas representing open air:

![grid layout of level1](https://i.imgur.com/41dECqx.png)

Below is the sequence of moves to solve this map, numbered and highlighted in blue.

![sequence of moves for level1](https://i.imgur.com/U48beYb.png)

and another possible solution:

![alternative sequence of moves for level1](https://i.imgur.com/BBZtM4w.png)

## Technical Details
- Input will always be valid and there will always be a solution.
- The block always begins in an upright position.
- The maximum grid size will be `15 x 20` (rows x colums)

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
