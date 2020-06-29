<!-- Stable Weight Arrangement -->
Here is a simple task. Take an array/tuple of unique positive integers, and two additional positive integers. Here's an example below:

```javascript
const arr = [3,5,7,1,6,8,2,4];
const n = 3; // span length
const q = 13; // weight threshold
```
```python
arr = (3,5,7,1,6,8,2,4)
n = 3 # span length
q = 13 # weight threshold
```
```go
var arr = []int{3,5,7,1,6,8,2,4}
var n int = 3 // span length
var q int = 13 // weight threshold
```

Try to re-arrange `arr` so that the sum of any `n` consecutive values does not exceed `q`.

```javascript
solver(arr,n,q); // one possible solution: [4,7,1,5,6,2,3,8]
```
```python
solver(arr,n,q) ## one possible solution: (4,7,1,5,6,2,3,8)
```
```go
Solver(arr,n,q) // one possible solution: {4,7,1,5,6,2,3,8}
```

Did you succeed? Great! Now teach a computer to do it.

<h2 style='color:#f88'>Technical Details</h2>

- All test inputs will be valid
- All test cases will have `0` or more possible solutions
- If a test case has no solution, return an empty array/tuple
- Test constraints:
  - `2 <= n <= 6`
  - `4 <= arr length < 12`
  - `n < arr length`
  - Every value in `arr` will be less than `q`
  - `11` fixed tests, `25` random tests
- In JavaScript, `module` and `require` are disabled
- For JavaScript, use Node 10+
- For Python, use Python 3.6+

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
