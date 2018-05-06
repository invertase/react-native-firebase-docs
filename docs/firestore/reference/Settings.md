# Settings

Specifies custom configurations for your Cloud Firestore instance. You must set these before invoking any other methods.

## Properties

### host
[method]host returns nullable boolean;[/method]

The hostname to connect to.

### persistence
[method]persistence returns nullable boolean;[/method]

Whether to use persistence.

### ssl
[method]ssl returns nullable boolean;[/method]

Whether to use SSL when connecting.

## Unsupported Properties

### timestampsInSnapshots
[method]timestampsInSnapshots returns nullable boolean;[/method]

!> Currently will have no effect, as it is not supported on both iOS and Android.

Enables the use of `Timestamp`s for timestamp fields in `DocumentSnapshot`s.

Currently, Firestore returns timestamp fields as `Date` but `Date` only supports millisecond precision, which leads to truncation and causes unexpected behavior when using a timestamp from a snapshot as a part of a subsequent query.
   
Setting `timestampsInSnapshots` to true will cause Firestore to return `Timestamp` values instead of `Date` avoiding this kind of problem. To make this work you must also change any code that uses `Date` to use `Timestamp` instead.

NOTE: in the future `timestampsInSnapshots: true` will become the default and this option will be removed so you should change your code to use Timestamp now and opt-in to this new behavior as soon as you can.