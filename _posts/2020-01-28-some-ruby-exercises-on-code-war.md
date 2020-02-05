---
layout: post
title: Some ruby exercises on codewar
category: Dev
tags: [dev, ruby]
---

My profile của codewar:
<img src="https://www.codewars.com/users/hientuminh/badges/large
"/>

## ROT13
### Details
How can you tell an extrovert from an introvert at NSA? Va gur ryringbef, gur rkgebireg ybbxf ng gur BGURE thl'f fubrf.

I found this joke on USENET, but the punchline is scrambled. Maybe you can decipher it? According to Wikipedia, ROT13 (http://en.wikipedia.org/wiki/ROT13) is frequently used to obfuscate jokes on USENET.

Hint: For this task you're only supposed to substitue characters. Not spaces, punctuation, numbers etc. Test examples:
```
rot13("EBG13 rknzcyr.") == "ROT13 example.";
rot13("This is my first ROT13 excercise!" == "Guvf vf zl svefg EBG13 rkprepvfr!"
```
### Solution
- **Hint** : https://ruby-doc.org/core-2.6/String.html#method-i-tr
```ruby
def rot13(message)
  input = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz'
  output = 'NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm'
  msg = []
  message.chars.each do |char|
    index = input.index(char)
    msg << if index
      output[index] 
    else
      char
    end
  end
  msg.join()
end
```

### Other solutions
```ruby
def rot13(message)
  p message.tr('a-zA-Z', 'n-za-mN-ZA-M')
end
```
```ruby
def rot13(message)
  #your code here
  a = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz".chars
  b = "NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm".chars
 message.chars.each.map { |x| (a.include?(x) ? b[a.index(x)] : x) }.join
end
```
```ruby
def rot13(message)
  message.chars.map do |c|
    case c
    when 'a'..'m', 'A'..'M' then (c.ord + 13).chr
    when 'm'..'z', 'N'..'Z' then (c.ord - 13).chr
    else c
    end
  end.join
end
```
## Replace With Alphabet Position
### Details
Welcome.

In this kata you are required to, given a string, replace every letter with its position in the alphabet.
If anything in the text isn't a letter, ignore it and don't return it.
> "a" = 1, "b" = 2, etc.

Example

```ruby
alphabet_position("The sunset sets at twelve o' clock.")
```
Should return
> "20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11" (as a string)
### Solutions
```ruby
def alphabet_position(text)
  text.gsub(/\s+/, "").chars.inject([]) do |str, char|
   if (char.upcase.ord >= 65 && char.upcase.ord <= 90)
     str << char.upcase.ord - 64
   end
   str
  end.join(' ')
end
```
### Other solutions
```ruby
def alphabet_position(text)
  text.gsub(/[^a-z]/i, '').chars.map{ |c| c.downcase.ord - 96 }.join(' ')
end
```
```ruby
P = ->(c) { c.ord - 64 }

def alphabet_position(text)
  text.upcase.scan(/[A-Z]/).map(&P).join(' ')
end
```
```ruby
def alphabet_position(text)
  text.upcase.tr('^A-Z', '').chars.map { |c| c.ord - 64 }.join(' ')
end
```

## Mean Square Error
### Details
Complete the function that:
- accepts two integer arrays of equal length
- compares the value each member in one array to the corresponding member in the other
- squares the absolute value difference between those two values
- and returns the average of those squared absolute value difference between each member pair.
```
[1, 2, 3], [4, 5, 6]              -->   9   because (9 + 9 + 9) / 3
[10, 20, 10, 2], [10, 25, 5, -2]  -->  16.5 because (0 + 25 + 25 + 16) / 4
[-1, 0], [0, -1]                  -->   1   because (1 + 1) / 2
```
### Solution
```ruby
def solution (arr1, arr2)
  length = arr1.length
  (0...length).inject(0) { |sum, index|
    sum +  ((arr1[index] - arr2[index]).abs)**2
  } / length.to_f
end
```
### Other solutions
- Using sum, fdiv
```ruby
def solution (arr1, arr2)
  arr1.map.with_index { |n, i| (n - arr2[i]).abs ** 2 }.sum.fdiv(arr1.length)
end
```
- Using Zip
```ruby
def solution (arr1, arr2)
  arr1.zip(arr2).sum { |a, b| (a-b)**2 } .fdiv(arr1.size)
end
```
- In JS
```javascript
function solution(a, b) {
  return a.reduce(function(s, n, i) { return s + Math.pow(n - b[i], 2) }, 0) / a.length;
}
```
## Number of trailing zeros of N!
### Details
> N! = 1 * 2 * 3 * ... * N

Be careful 1000! has 2568 digits...

For more info, see: http://mathworld.wolfram.com/Factorial.html

Examples
```
zeros(6) = 1
# 6! = 1 * 2 * 3 * 4 * 5 * 6 = 720 --> 1 trailing zero

zeros(12) = 2
# 12! = 479001600 --> 2 trailing zeros
```
*Hint: You're not meant to calculate the factorial. Find another way to find the number of zeros.*
### My Solution
```ruby
def zeros(n)
  i = 5
  count = 0
  while ( n / i >= 1)
    count = count + n / i
    i = i * 5
  end
  count
end
```
### Other solutions
- Recursion
```ruby
def zeros(n)
  n < 5 ? 0 : (n / 5) + zeros(n / 5)
end
```
- Loop
```ruby
def zeros(n)
  zeros = 0
  zeros += n /= 5 while n >= 1
  zeros
end
```
## Create Phone Number
### Details
Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example
```
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]) # => returns "(123) 456-7890"
```
The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!
### My Solution
```ruby
def createPhoneNumber(str)
  "(#{str[0..2].join}) #{str[3..5].join}-#{str[6..10].join}"
end
```
### Other solutions
- Format array
```ruby
def createPhoneNumber(array)
  '(%d%d%d) %d%d%d-%d%d%d%d' % array
end
```
- Using slide
```ruby
def createPhoneNumber(digits)
  area_code, prefix, *extension = digits.each_slice(3).map(&:join)
  "(#{area_code}) #{prefix}-#{extension.join}"
end
```