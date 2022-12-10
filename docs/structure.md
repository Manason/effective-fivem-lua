# Structure/Scope

## Prefer Limited Scope
Variables and functions should be scoped to the smallest visibility needed. Prefer in order: local, global, export

## Separate Client & Server Files
Client and server specific files should be organized into their own folders

## Group Related Functions
local single use functions should be located directly underneath or as close as possible to their calling functions. Functions which can be logically grouped together should be located near to each other within a file

## Use Files To Hide Local Functions
If you have one resource scoped function which calls a few local single use functions, put them all in their own file.

## Resource Naming
Resources should be named with underscores "_" instead of spaces. Other Special characters should be avoided so that exports work well.

## File Naming
Files should be named all lower case without any spaces. dashes "-" or underscores "_" can be used instead of spaces.