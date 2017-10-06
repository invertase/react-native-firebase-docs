# Trace

> Once a trace has been started and stopped, you cannot re-start it in the same app lifecycle.

## start
[method]trace.start() returns void;[/method]

Initializes the trace to start tracing performance to relay back to Firebase.

## incrementCounter
[method]trace.incrementCounter(event) returns void;[/method]

Notifies Firebase an event has occured. These events will be visible on Firebase once your trace has stopped.

| Parameter |         |
| --------- | ------- |
| event     | **string** <br /> An event name to increment a counter against |

## stop
[method]trace.stop() returns void;[/method]

Stops performance tracing. The completed trace stats are now sent to Firebase.

> Results are not realtime. They can take a number of hours to appear in the Firebase console.
