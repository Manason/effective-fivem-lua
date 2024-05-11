# Conditionals

## Default Values
Consider [ternary operator](http://lua-users.org/wiki/TernaryOperator) 'or' instead of nil checks to improve readability.
```lua title="BAD"
if name then
    return name
else
    return "John Doe"
end
```
```lua title="GOOD"
return name or "John Doe"
```

## Don't Write "if true then return true"
When returning or setting a variable to the value of the conditional statement itself, don't use an if else block.
```lua title="BAD"
if name == "mark" or name == "stacy" then
   return true
else
   return false
end
```
```lua title="GOOD"
return name == "mark" or name == "stacy"
```

## Prefer positive boolean expressions
This makes the code easier to read.
```lua title="BAD"
if not isHappy then
  return "sad"
else
  return "happy"
end
```
```lua title="GOOD"
if isHappy then
  return "happy"
else
  return "sad"
end
```
