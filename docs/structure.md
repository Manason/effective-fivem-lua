# Structure/Scope

## Prefer Limited Scope
Variables and functions should be scoped to the smallest visibility needed. Prefer in order
| Function         | Visibility      |
|------------------|-----------------|
| local function   | file            |
| function         | resource        |
| export function  | client/server   |
| AddEventHandler  | client/server   |
| RegisterNetEvent/Callback | shared |


## Separate Client & Server Files
Client and server specific files should be organized into their own folders

## Use Logical Grouping
It may make sense to place constructs of the same type together in a file. For example, all file scoped variables at the top of the file, followed by all local functions, followed by all global functions, followed by events. This grouping structure makes it easier to understand the API at the server, resource, and file levels. Alternatively, local single use functions could be located directly above or as close as possible to the functions they are called from, and grouping can be based on call structure rather than construct type.

## Use Files To Hide Local Functions
If you have one resource scoped function which calls a few local single use functions, put them all in their own file.

## Resource Naming
Resources should be named with underscores "_" instead of spaces. Other Special characters should be avoided so that exports work well.

## File Naming
Files should be named all lower case without any spaces. dashes "-" or underscores "_" can be used instead of spaces.
