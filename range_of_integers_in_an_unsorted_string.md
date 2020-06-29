<!--Range of Integers in an Unsorted String-->
<p>In this kata, your task is to write a function that returns the smallest and largest integers in an unsorted string. In this kata, a range is considered a finite sequence of consecutive integers.</p>

<h2 style='color:#f88'>Input</h2>
Your function will receive two arguments:
<ul>
	<li>A <code>string</code> comprised of integers in an unknown range; think of this string as the result when a range of integers is shuffled around in random order then joined together into a string</li>
	<li>An <code>integer</code> value representing the size of the range</li>
</ul>

<h2 style='color:#f88'>Output</h2>
Your function should return the starting (minimum) and ending (maximum) numbers of the range in the form of an array/list comprised of two integers.

<h2 style='color:#f88'>Test Example</h2>

```python
input_string = '1568141291110137'

mystery_range(input_string, 10) # [6, 15]

# The 10 numbers in this string are:
# 15 6 8 14 12 9 11 10 13 7
# Therefore the range of numbers is from 6 to 15
```

```javascript
let inputString = '1568141291110137';

mysteryRange(inputString, 10) // [6, 15]

// The 10 numbers in this string are:
// 15 6 8 14 12 9 11 10 13 7
// Therefore the range of numbers is from 6 to 15
```

```go
inputString := "1568141291110137"
MysteryRange(inputString, 10) // [6 15]

// The 10 numbers in this string are:
// 15 6 8 14 12 9 11 10 13 7
// Therefore the range of numbers is from 6 to 15
```

```elixir
# For Elixir, return a tuple
input_string = "1568141291110137"

KataSolution.mystery_range(input_string, 10) # {6, 15}

# The 10 numbers in this string are:
# 15 6 8 14 12 9 11 10 13 7
# Therefore the range of numbers is from 6 to 15
```

```csharp
string input_string = "1568141291110137";
KataSolution.MysteryRange(input_string, 10); // [6, 15]

// The 10 numbers in this string are:
// 15 6 8 14 12 9 11 10 13 7
// Therefore the range of numbers is from 6 to 15
```

```ruby
input_string = '1568141291110137'

mystery_range(input_string, 10) # [6, 15]

# The 10 numbers in this string are:
# 15 6 8 14 12 9 11 10 13 7
# Therefore the range of numbers is from 6 to 15
```

<h2 style='color:#f88'>Technical Details</h2>
<ul>
	<li>The maximum size of a range will be <code>100</code> integers</li>
	<li>The starting number of a range will be: <code>0 < n < 100</code></li>
	<li>Full Test Suite: <code>21</code> fixed tests, <code>100</code> random tests</li>
	<li>Use Python 3+ for the Python translation</li>
	<li>For JavaScript, <code>require</code> has been disabled and most built-in prototypes have been frozen (prototype methods can be added to <code>Array</code> and <code>Function</code>)</li>
	<li>All test cases will be valid</li>
</ul>

<p>If you enjoyed this kata, be sure to check out <a href='https://www.codewars.com/users/docgunthrop/authored' style='color:#9f9;text-decoration:none'>my other katas</a></p>
