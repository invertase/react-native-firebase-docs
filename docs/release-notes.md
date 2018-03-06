# v3.3.0 Changelog

TL;DR: Main focus of this release is Cloud Firestore Transaction support + minor bug fixes and SDK version upgrades.

### Cloud Firestore

- [`firestore.runTransaction()`](https://rnfirebase.io/docs/v3.3.x/firestore/transactions) - Implemented transaction support 

### Analytics 

- [`analytics.logEvent()`](https://rnfirebase.io/docs/v3.3.x/analytics/reference/analytics#Methods) - added additional argument validations (fixes #846)

### Auth 

- Add missing `reauthenticateAndRetrieveDataWithCredential` native methods

### Crashlytics

- [android] updated Crashlytics native SDK to v2.9.1

### Other

- [internals] remove bows logger dependency + window shims (fixes #858)
