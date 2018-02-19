# Reserved Events

A number of methods are provided to help tailor analytics specifically for your own app, however the Firebase SDK includes a number of pre-set events which are automatically handled and cannot be used with custom [logEvent](version /analytics/reference/analytics#logevent) events. 

!> Attempting to use one of these events will throw an exception.


```js
const reserved = [
  'app_clear_data',
  'app_uninstall',
  'app_update',
  'error',
  'first_open',
  'first_visit',
  'first_open_time',
  'first_visit_time',
  'in_app_purchase',
  'notification_dismiss',
  'notification_foreground',
  'notification_open',
  'notification_receive',
  'os_update',
  'session_start',
  'screen_view',
  'user_engagement',
  'ad_impression',
  'ad_click',
  'ad_query',
  'ad_exposure',
  'adunit_exposure',
  'ad_activeiew',
];
```
