# Functions

Functions should only do one thing, and should be small. If a function is not small, break it up into smaller functions.

## Naming
Functions should be named in camelCase format to differentiate from natives and standard lua library functions

Functions should also be named with a leading verb.

```lua title="BAD"
function player()
function playerDrop()
```
```lua title="GOOD"
function getPlayerObject()
function dropPlayer()
```

## Avoid passing implied functions as arguments
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

## Exports
Exports should export local functions and have a [lua-language-server annotation](https://github.com/sumneko/lua-language-server/wiki/Annotations) to delare the API
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

## Be careful overloading a function. Consider using an overloaded function as a wrapper to transform to a standard format which is then calls a local function. Overloading can be a smell that a function is doing more than one thing.

## Put required parameters before optional parameters
