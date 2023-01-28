# Functions

## Size & Scope
- Functions should only do one thing, and should be small. If a function is not small, break it up into smaller functions.
- Every line of a function should be at the same abstraction level, which should be one smaller than the name of the function.
- Functions should normally not be more than 6-10 lines long. A long function is a sign that it may be doing more than one thing, or maybe including low level code mixed with high level code.

## Naming
- Local functions should be named in camelCase format to differentiate from natives and standard lua library functions
- Global functions should named in PascalCase format
- Functions should also be named with a leading verb.

```lua title="BAD"
function player()
function playerDrop()
```
```lua title="GOOD"
function getPlayerObject()
function dropPlayer()
```

## Parameters

### Limit Number of Parameters
If needing more than 3 or so parameters for a single function, that may be a sign that the parameters can be grouped within a table and passed as a object, rather than as individual arguments.
```lua title="BAD"
function createChar(name, age, height, birthday, nationality)

end
```
```lua title="GOOD"
function createChar(char)

end
```

### Avoid boolean parameters
Boolean parameters are a signal that a function is doing two things. Instead, call two different functions that each do one thing.
```lua title="BAD"
function printEmotionalState(isHappy)
    if isHappy then
        print("happy")
    else
        print("sad")
    end
end
```
```lua title="GOOD"
function printHappy()
    print("happy")
end

function printSad()
    print("sad")
end
```

### Avoid passing implied functions as arguments
Instead declare the function in a local variable and pass the variable as the argument. This has major performance improvements if the calling function is invoked more than once. Some functions such as CreateThread are often only invoked once, so there wouldn't be any performance improvement to localizing the argument function. However, I still recommend it anyway as a defensive measure to avoid the issue entirely if the code were to change in the future.

```lua title="BAD"
someFunction(function()

end)
```
```lua title="GOOD"
local myFunction = function()

end
someFunction(myFunction)
```

### Parameter Overloads
Be careful overloading a function. Overloading can be a smell that a function is doing more than one thing. Overloads are useful as wrapper functions, providing different ways to call the same underlying function.

### Optional Parameters
Required parameters should come before optional ones.

## Export Documentation
Exports should have a [lua-language-server annotation](https://github.com/sumneko/lua-language-server/wiki/Annotations) to delare the API
```lua
--- Puts a space between a first and last name
---@param first string first name
---@param last string last name
---@return string full name
local function formatName(first, last)
    return first .. ' ' .. last
end

exports('formatName', formatName)
```

## Avoid Nesting
Use guard clauses to invert if else clauses or extract additional functions. Nesting makes code difficult to read and is a smell that a function may be doing more than one thing
```lua title="BAD"
local function getFullName(first, last)
    if first and last then
        return first .. last
    else
        return nil
    end
end
```
```lua title="GOOD"
local function getFullName(first, last)
    if not first or not last then return end
    return first .. last
end
```
