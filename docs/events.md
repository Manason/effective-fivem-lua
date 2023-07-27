# Events

## Naming
Event names should be in the form '{resourceName}:{client/server}:{eventName}'
This allows the reader to tell at a glance what resource the event is triggered from, and whether the event should be handled on the client or server.

### Past Tense
An event should describe something that has already happened, without prescribing the desired reaction. This pattern recognizes that many event handlers may exist for the same event, which each handle the event in a different way. Triggering an event should be thought of as the cause, whereas handling an event is the effect. The effect should not be in the event name. While an event name need not strictly be past tense, writing event names using past tense can help developers follow this principle.

```lua title="BAD"
local function sendMessage(message)
    TriggerEvent('resourceName:server:checkProfanity', message)
end

RegisterNetEvent('resourceName:server:checkProfanity', source, message)
    checkProfanity(message)
end
```
```lua title="GOOD"
local function sendMessage(message)
    TriggerEvent('resourceName:server:sentMessage', message)
end

RegisterNetEvent('resourceName:server:sentMessage', source, message)
    checkProfanity(message)
end
```

## Use callbacks when wanting to get data back across the network
It's an anti-pattern to trigger and listen for a separate event to get data back across the network when triggering an event. Instead, use a callback.

## Use a function instead of an event handler for single resource, non-networked events
Events differ from functions in that one event can have many handler functions, versus a function call only executes one function. If the event is non-networked and only is intended to be handled by one resource, a function should be used instead.

## Use AddEventHandler for non-networked events
Keeping with the principle of limiting scope, if an event is triggered and handled on the client or server exclusively, do not register it as a net event.

## Secure Net Events
GetInvokingResource will be nil if an event is triggered from the opposite side of the network that the event is registered on (client triggering a server event, or server triggering a client event). Restrict other ways to call the event to prevent exploits, unless the event is intended to be triggered by both the client and server.
```lua
RegisterNetEvent('resourceName:client:eventName', function()
    if GetInvokingResource() then return end
    --- handle the event
end)
```
