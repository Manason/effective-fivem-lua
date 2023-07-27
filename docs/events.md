# Events

## Naming
Event names should be in the form '{resourceName}:{client/server}:{eventName}'
This allows the reader to tell at a glance what resource the event is triggered from, and whether the event should be handled on the client or server.

### Past Tense
An event should describe something that has already happened, without prescribing the desired reaction. This pattern recognizes that many event handlers may exist for the same event, which each handle the event in a different way. Therefore, event names should be past tense.

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
