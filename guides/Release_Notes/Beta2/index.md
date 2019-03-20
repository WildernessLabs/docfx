# Meadow Beta 2

## New Features

### Analog Input

### Notifications + `IObservable` Reactive Pattern

## Fixed Bugs

* [Threads Fail](https://github.com/WildernessLabs/Meadow_Issues/issues/1)

## Known Issues

* [Tasks Behave Strangely](https://github.com/WildernessLabs/Meadow_Issues/issues/2) - Workaround is to use `Thread`, as seen in the [Basic_Threading](https://github.com/WildernessLabs/Meadow.Core/tree/master/source/Tests/Basic_Threading) sample app.
* [`Debug.Write` calls don't output to the console](https://github.com/WildernessLabs/Meadow_Issues/issues/3) - Workaround is to use `Console.Write` calls.