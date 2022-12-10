# Conditionals

## Default Values
Use 'or' Instead of nil Checks for erformance and readability optimization.
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

## Avoid nil in Comparisons involving non-boolean values

### Implied ~= nil
```lua title="BAD"
if myVariable ~= nil
```
```lua title="GOOD"
if myVariable
```

### not instead of '== nil'
```lua title="BAD"
if myVariable == nil
```
```lua title="GOOD"
if not myVariable
```