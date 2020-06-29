### Welcome to the Challenge Edition of *Upside-Down Numbers*

In the [original kata by @KenKamau](https://www.codewars.com/kata/59f7597716049833200001eb) you were limited to integers below `2^17`. Here, you will be given strings of digits of up to `42` characters in length (upper bound is `10^42 - 1`).

Your task is essentially the same, but an additional challenge is creating a fast, efficient solution.

### Input:
Your function will receive two strings, each comprised of digits representing a positive integer. These two values will represent the upper and lower bounds of a range.

### Output:
Your function must return the number of valid upside down numbers within the range of the two input arguments, including both upper and lower bounds.

### What is an Upside-Down Number?
An upside down number is an integer that appears the same when rotated 180 degrees, as illustrated below.

![1961 - OK, 88 - OK, 101 - OK, 25 - No](https://i.imgur.com/Biixbsd.png)

**Example:**
```javascript
const x = '0',
	  y = '25';
upsideDown(x,y); //4
//the valid numbers in the range are 0, 1, 8, and 11
```
```python
x = '0'
y = '25'
upsidedown(x,y) #4
# the valid numbers in the range are 0, 1, 8, and 11
```
```go
var x,y string = "0","25"
upsideDown(x,y); //4
//the valid numbers in the range are 0, 1, 8, and 11
```
```csharp
string x = "0", y = "25";
UpsideDownNumbers.UpsideDown(x, y); //4
//the valid numbers in the range are 0, 1, 8, and 11
```

### Additional Notes:
- All inputs will be valid.
- The first argument will always be less than the second argument (ie. the range will always be valid).


If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
