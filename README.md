# Recursion Problems

## Definitions
Define the following: 

- Recursion = method that calls itself within the method; the opposite of iterative
- Recursive Case = a problem that divides the problem into a smaller problem
- Base Case = a problem that can be solved immediately, it returns a result without recursion and is used to stop it
- Activation Chain/Stack = all of the individual recursive calculations for the given value (all of the "bubbles")
- Activation Record/Call = one stack frame, which is the memory used to store local variables; single invocation of a method (each of the "bubbles")
- Infinite Recursion/Stack Overflow/Stack too deep = the recuriosn would never stop, there is no base case
- Tail Recursion = a form of recursive programming, where the recursive call is the last call in any given method

## Tracing through a recursive method

### Trace #1
```
def mystery1(n)
  if n == 1
    return n
  else
    return n + mystery1(n-1)
  end
end
```

- What is mystery1(5)? 15
- What is mystery1(10)? 55
- What is mystery1(0)? infinite recursion

### Trace #2
```
def mystery2(n)
  if n < 10
    return n
  else
    return (n%10) + mystery2(n/10)
  end
end
```

- What is mystery2(123)? 6
- What is mystery2(9005)? 14
- What is mystery2(-123)? -123
- _Added Fun: How could we make `mystery2(-123)` work the way we might expect it to work instead of the way it does?_

### Trace #3
```
def mystery3(n)
  if n == 0
    return 100
  elsif n == -1
    return 200
  end
  if n%2 == 0
    return mystery3(n/2)
  else
    return mystery3(n-1)
  end
end
```

- What is mystery3(1)? 100
- What is mystery3(13)? 100
- What is mystery3(-6)? 200

### Trace #4
```
def mystery4(b,e)
  if e == 0
    return 1
  else
    return b * mystery4(b,e-1)
  end
end
```

- What is mystery4(10,2)? 100
- What is mystery4(4,3)? 64
- What is mystery4(5,0)? 1

### Trace #5
```
def mystery5(s)
  if s.length == 0
    return ""
  else
    return "*" + mystery5(s[1..-1])
  end
end
```

- What is mystery5("hi")? "**"
- What is mystery5("")? ""
- What is mystery5("Hi, there!")? "**********"
- _Added Fun: How could we make only alphabetic characters to be changed to stars?_

### Trace #6
```
def mystery6(s)
  if s == nil || s.length == 0
    return ""
  else
    space = 0
    until space >= s.length || s[space] == " "
      space += 1
    end
    return mystery6(s[(space+1)..-1]) + " " + s[0...space]
  end
end
```

- What is mystery6("goodnight moon")? "moon goodnight"
- What is mystery6("Ada Developers Academy")? "Developers Academy Ada"
- What is mystery6("Hi, there!")? "there! Hi,"
- _Added Fun: How could we make the reversal happen by letter, instead of by word (i.e. Make it so that mystery6("goodnight moon") returned "noom thgindoog")?_
