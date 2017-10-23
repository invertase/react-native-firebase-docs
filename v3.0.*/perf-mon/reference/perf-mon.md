# Performance Monitoring

```
firebase.perf
```

Firebase Performance Monitoring captures a number of traces automatically, such as all outbound HTTP requests, app boot time and more.

## Methods 

The following methods are accessed via the Performance Monitoring instance `firebase.perf()`.

### setPerformanceCollectionEnabled
[method]setPerformanceCollectionEnabled(enabled) returns void;[/method]

Enables or disables performance monitoring. 

[collapse Example]
```js
firebase.perf().setPerformanceCollectionEnabled(false);
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| enabled   | **boolean** <br />Whether monitoring is enabled or disabled |

### newTrace
[method]newTrace(id) returns [ref perf-mon.Trace];[/method]

Returns a new instance of Trace. The id is the unique name of something you'd like to run performance monitoring against.

[collapse Example]
```js
const trace = firebase.perf().newTrace('authentication');
trace.start();
```
[/collapse]

| Parameter |         |
| --------- | ------- |
| id   | **string** <br /> The unique name of the trace to monitor |

## Classes

### Trace

[ref perf-mon.Trace]
