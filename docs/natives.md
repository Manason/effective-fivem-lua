# Natives

## Remove Citizen. prefix where possible
```lua title="BAD"
Citizen.Wait()
Citizen.CreateThread()
Citizen.SetTimeout()
```
```lua title="GOOD"
Wait()
CreateThread()
SetTimeout()
```

## Do not use GetHashKey()

### Replace string hashes with backticks
```lua title="BAD"
local hashKey = GetHashKey('hash')
```
```lua title="GOOD"
local hashKey = `hash`
```

### Replace GetHashKey(variable) with joaat(variable)
```lua title="BAD"
local hashKey = GetHashKey(myHash)
```
```lua title="GOOD"
local hashKey = joaat(myHash)
```

## Use Vector3 math rather than GetDistanceBetweenCoords()
```lua title="BAD"
local distance = GetDistanceBetweenCoords(1, 1, 1, 0, 0, 0)
```
```lua title="GOOD"
local coord1 = vector3(1, 1, 1)
local coord2 = vector3(0, 0, 0)
local distance = #(coord1 - coord2)
```

## Use PlayerPedId() instead of GetPlayerPed(-1)
```lua title="BAD"
local playerPed = GetPlayerPed(-1)
```
```lua title="GOOD"
local playerPed = PlayerPedId()
```
