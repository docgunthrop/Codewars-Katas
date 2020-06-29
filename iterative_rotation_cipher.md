In this kata, your task is to implement what I call **Iterative Rotation Cipher (IRC)**. To complete the task, you will create an object with two methods, `encode` and `decode`. (For non-JavaScript versions, you only need to write the two functions without the enclosing dict)

<h2 style='color:#f66'>Input</h2>
<p>The <code>encode</code> method will receive two arguments — a positive integer <code>n</code> and a string value.</p>
<p>The <code>decode</code> method will receive one argument — a string value.</p>

<h2 style='color:#f66'>Output</h2>
<p>Each method will return a string value.</p>

<h2 style='color:#f66'>How It Works</h2>
<p>Encoding and decoding are done by performing a series of character and substring rotations on a string input.</p>
<p><strong style='color:#95c4ffff'>Encoding:</strong> The number of rotations is determined by the value of <code>n</code>. The sequence of rotations is applied in the following order:<br/>
&emsp;Step 1: remove all spaces in the string (but remember their positions)<br/>
&emsp;Step 2: shift the order of characters in the new string to the right by <code>n</code> characters<br/>
&emsp;Step 3: put the spaces back in their original positions<br/>
&emsp;Step 4: shift the characters of each substring (separated by one or more consecutive spaces) to the right by <code>n</code><br/>
</p>
<p>Repeat this process until it has been completed <code>n</code> times in total.<br/>
The value <code>n</code> is then prepended to the resulting string with a space.</p>
<p><strong style='color:#95c4ffff'>Decoding:</strong> Decoding simply reverses the encoding process.</p>

<h2 style='color:#f66'>Test Example</h2>

```javascript
let quote = `If you wish to make an apple pie from scratch, you must first invent the universe.`;
let solution = `10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet`;
IterativeRotationCipher.encode(10,quote) === solution; //true


/* Step-by-step breakdown:
Step 1 — remove all spaces:
`Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse.`

Step 2 — shift the order of string characters to the right by 10:
`euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth`

Step 3 — place the spaces back in their original positions:
`eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth`

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
`eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt`

Repeat the steps 9 more times before returning the string with `10 ` prepended.
*/
```
```haskell
quote = "If you wish to make an apple pie from scratch, you must first invent the universe."
solution = "10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet"
IterativeRotationCipher.encode(10,quote) == solution -- True


{- Step-by-step breakdown:
Step 1 — remove all spaces:
"Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse."

Step 2 — shift the order of string characters to the right by 10:
"euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth"

Step 3 — place the spaces back in their original positions:
"eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth"

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
"eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt"

Repeat the steps 9 more times before returning the string with "10 " prepended.
-}
```
```python
quote = 'If you wish to make an apple pie from scratch, you must first invent the universe.'
solution = '10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet'
IterativeRotationCipher['encode'](10,quote) == solution; //True


'''Step-by-step breakdown:
Step 1 — remove all spaces:
'Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse.'

Step 2 — shift the order of string characters to the right by 10:
'euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth'

Step 3 — place the spaces back in their original positions:
'eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth'

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
'eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt'

Repeat the steps 9 more times before returning the string with '10 ' prepended.
'''
```
```ruby
quote = 'If you wish to make an apple pie from scratch, you must first invent the universe.'
solution = '10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet'
encode(10,quote) == solution # true


Step 1 — remove all spaces:
'Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse.'

Step 2 — shift the order of string characters to the right by 10:
'euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth'

Step 3 — place the spaces back in their original positions:
'eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth'

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
'eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt'

Repeat the steps 9 more times before returning the string with '10 ' prepended.
```
```go
quote := `If you wish to make an apple pie from scratch, you must first invent the universe.`;
solution := `10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet`;
IterativeRotationCipher.encode(10,quote) == solution; //true


/* Step-by-step breakdown:
Step 1 — remove all spaces:
`Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse.`

Step 2 — shift the order of string characters to the right by 10:
`euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth`

Step 3 — place the spaces back in their original positions:
`eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth`

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
`eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt`

Repeat the steps 9 more times before returning the string with `10 ` prepended.
*/
```
```elixir
phrase = "If you wish to make an apple pie from scratch, you must first invent the universe."
solution = "10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet"
IterativeRotationCipher.encode(10,phrase) == solution ##true


# Step-by-step breakdown:
# Step 1 — remove all spaces:
# "Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse."

# Step 2 — shift the order of string characters to the right by 10:
# "euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth"

# Step 3 — place the spaces back in their original positions:
# "eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth"

# Step 4 — shift the order of characters for each space-separated substring to the right by 10:
# "eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt"

# Repeat the steps 9 more times before returning the string with "10 " prepended.
```
```csharp
string phrase = "If you wish to make an apple pie from scratch, you must first invent the universe.";
string solution = "10 hu fmo a,ys vi utie mr snehn rni tvte .ysushou teI fwea pmapi apfrok rei tnocsclet";
IterativeRotationCipher.Encode(10,phrase) == solution // true

/* Step-by-step breakdown:
Step 1 — remove all spaces:
"Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventtheuniverse."

Step 2 — shift the order of string characters to the right by 10:
"euniverse.Ifyouwishtomakeanapplepiefromscratch,youmustfirstinventth"

Step 3 — place the spaces back in their original positions:
"eu niv erse .I fyou wi shtom ake anap plepiefr oms crat ch,yo umustf irs tinventth"

Step 4 — shift the order of characters for each space-separated substring to the right by 10:
"eu vni seer .I oufy wi shtom eak apan frplepie som atcr ch,yo ustfum sir htinventt"

Repeat the steps 9 more times before returning the string with "10 " prepended. */
```

<h2 style='color:#f66'>Technical Details</h2>

- Input will always be valid.
- The characters used in the strings include any combination of alphanumeric characters, the space character, the newline character, and any of the following: `_!@#$%^&()[]{}+-*/="'<>,.?:;`.

If you enjoyed this kata, be sure to check out [my other katas](https://www.codewars.com/users/docgunthrop/authored).
