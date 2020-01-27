---
layout: post
title: Một số bài tập ruby trên codewar
category: Dev
tags: [dev, ruby]
---

My profile của codewar:
<img src="https://www.codewars.com/users/hientuminh/badges/large
"/>

## Number of trailing zeros of N!
### Đề bài
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
### Bài giải
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
### Một số bài giải trên diễn đàn
- Đệ quy
```ruby
def zeros(n)
  n < 5 ? 0 : (n / 5) + zeros(n / 5)
end
```
- Vòng lặp
```ruby
def zeros(n)
  zeros = 0
  zeros += n /= 5 while n >= 1
  zeros
end
```