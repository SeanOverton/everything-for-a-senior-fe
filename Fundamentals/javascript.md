# Javascript

## Module system

The module system only results in each imported file executing exactly once.
This means that objects that are initialized within a module and exported will be the same object used everywhere.

For example:
