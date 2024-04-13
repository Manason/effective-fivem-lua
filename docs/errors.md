# Error Handling

An unexpected state or condition within the code may cause a lua error to be thrown. However, these bad states can have other consequences when not so explicitly detected and handled. They may propagate bad state to other components of the system, or introduce unintended behavior. Checking for and handling unexpected state can make your code more robust to possibile failures and vulnerabilities.

## Use assert instead of 'if expression then error()'
assert is a more succinct, readable way to throw an error on a condition not being met

```lua title="BAD"
if not someVar then error("someVar is nil") end
```
```lua title="GOOD"
assert(someVar ~= nil, "someVar is nil")
```

## Pre-condition check liberally
When performing an operation, make a list of assumptions and then write pre-condition checks.

## Fail loudly for unexpected state
When writing pre-condition checks, failure should often result in a lua error with a message. Failing silently by just early returning from a function can be difficult to debug and may go undetected.

```lua title="BAD"
if not isPlayerDead() then return end
```
```lua title="GOOD"
assert(isPlayerDead(), "player is not dead")
```

## Throwing an Error vs Logging
Some states may be unexpected, but recoverable. In these cases, it may be preferable to log the state, but still allow the operation to proceed. An example of this would be a player selling items to an NPC. If some of the items were failing to sell, it would be better to log/print the error, while allowing the rest of the items to go through.

Keep in mind what execution will be cancelled by throwing an error and use best judgment to decide whether throwing or logging is the better choice.