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

## Do not pass an implied function as an argument
Instead declare the function in a local variable and pass the variable as the argument. This is a huge performance improvement and is often a readability one as well.

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
