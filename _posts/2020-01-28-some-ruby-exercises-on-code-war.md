---
layout: post
title: Some ruby exercises on codewar
category: Dev
tags: [dev, ruby]
---

My profile của codewar:
<img src="https://www.codewars.com/users/hientuminh/badges/large
"/>

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