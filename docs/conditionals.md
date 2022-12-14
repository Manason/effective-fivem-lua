# Conditionals

## Default Values
Use [ternary operator](http://lua-users.org/wiki/TernaryOperator) 'or' Instead of nil checks for performance and readability optimization.
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