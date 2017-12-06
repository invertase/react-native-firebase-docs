# ConfirmationResult

Returned as the result from [ref auth#signInWithPhoneNumber].

## Properties

### verificationId
[method]verificationId returns nullable string;[/method]

Returns this confirmation results unique ID.

## Methods

### confirm
[method]confirm(verificationCode) returns Promise containing [ref auth.User];[/method]

Confirms a verification request by passing in the verification code sent with the SMS.

| Parameter |         |
| --------- | ------- |
| verificationCode  | **string** <br /> Code sent with the SMS verification message. |
