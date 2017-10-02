# Error Handling

Errors returned from Admob are always returned as a JavaScript [Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error) containing a code and message.

| code                              | message                                                                                                      |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| admob/error-code-internal-error   | Something happened internally; for instance, an invalid response was received from the ad server.            |
| admob/error-code-invalid-request  | The ad request was invalid; for instance, the ad unit ID was incorrect.                                      |
| admob/error-code-network-error    | The ad request was unsuccessful due to network connectivity.                                                 |
| admob/error-code-no-fill          | The ad request was successful, but no ad was returned due to lack of ad inventory.                           |
| admob/os-version-too-low          | The current device’s OS is below the minimum required version.                                               |
