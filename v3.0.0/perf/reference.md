# Performance Monitoring

```
firebase.perf
```

## Methods 

### setPerformanceCollectionEnabled
*setPerformanceCollectionEnabled(enabled) returns void;*

Enables or disables performance monitoring. 

| Parameter |         |
| --------- | ------- |
| enabled   | **boolean** <br />W hether monitoring is enabled or disabled |

### newTrace
[method]newTrace(id) returns [Trace](#trace);[/method]

Returns a new instance of Trace. The id is the unique name of something you'd like to run performance monitoring against.

| Parameter |         |
| --------- | ------- |
| id   | **string** <br /> The unique name of the trace to monitor |

## Classes

### Trace

> Once a trace has been started and stopped, you cannot re-start it in the same app lifecycle.

#### start
*trace.start() returns void;*

Initializes the trace to start tracing performance to relay back to Firebase.

#### incrementCounter
*trace.incrementCounter(event) returns void;*

Notifies Firebase an event has occured. These events will be visible on Firebase once your trace has stopped.

| Parameter |         |
| --------- | ------- |
| event     | **string** <br /> An event name to increment a counter against |

#### stop
*trace.stop() returns void;*

Stops performance tracing. The completed trace stats are now sent to Firebase.

?> Results are not realtime. They can take a number of hours to appear in the Firebase console.
