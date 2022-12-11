# Variables

## Naming
### Name constants using ALL_CAPS
```lua
local MY_CONSTANT = "constant value"
MY_GLOBAL_CONSTANT = "another constant value"
```

### camelCase non-constant local variable names
```lua
local myVariable = "variable value"
```

### PascalCase non-constant global variable names
```lua
MyGlobalVariable = "global variable value"
```

### Use underscore "_" as the name of a variable that cannot be deleted but is unused.
```lua
local function printValues(map)
    for _, v in pairs(map) do
        print(v)
    end
end
```

