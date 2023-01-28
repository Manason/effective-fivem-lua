# Events

## Naming
Event names should be in the form '{resourceName}:{client/server}:{eventName}'
This allows the reader to tell at a glance what resource the event is triggered from, and whether the event should be handled on the client or server.

## Use a function instead of an event handler if only one event handler exists
Events differ from functions in that one event can have many handlers in different resources to take actions on the event. If the event is only intended to be handled by a specific resource, a function should be used instead.

## Use AddEventHandler for events that will not be passed over the network
Keeping with the principle of limiting scope, if an event is triggered and handled on the client or server exclusively, do not register it as a net event.


## Secure Net Events
GetInvokingResource will be nil if an event is triggered from the opposite side of the network that the event is registered on (client triggering a server event, or server triggering a client event). Since Net Events should be triggered across the network, restrict other ways to call the event to prevent exploits.
```lua
RegisterNetEvent('resourceName:client:eventName', function()
    if GetInvokingResource() then return end
    --- handle the event
end)
```
