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

## Location
Local variables within a function should be declared as close as possible to the place where they are used. This limits what the developer must keep in their head while reading the code.
Local variables declared outside of a function should be declared at the top of the file, grouped together.
Global variables should be declared at the top of the file grouped together. client/server global variables should only be declared within a single client/server file. This helps keep things organized instead of spreading random globals around the resource.

