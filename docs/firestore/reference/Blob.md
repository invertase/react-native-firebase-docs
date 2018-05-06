# Blob

```
firebase.firestore.Blob
```

## Static Methods

### fromBase64String
[method]fromBase64String(base64) returns [ref firestore.Blob];[/method]

Creates a new Blob from the given Base64 string, converting it to bytes.

| Parameter |         |
| --------- | ------- |
| base64  | **string** <br /> The Base64 string used to create the Blob object.|

[collapse Example]
```js
firebase.firestore.Blob.fromBase64String(base64string);
```
[/collapse]

### fromUint8Array
[method]fromUint8Array(array) returns [ref firestore.Blob];[/method]

Creates a new Blob from the given Uint8Array.

| Parameter |         |
| --------- | ------- |
| array  | **Uint8Array** <br /> The Uint8Array used to create the Blob object.<br />Value must not be null.|

[collapse Example]
```js
firebase.firestore.Blob.fromUint8Array(uint8Array);
```
[/collapse]

## Methods

### isEqual
[methods]isEqual(other) returns [ref firestore.Blob];[/methods]

Returns 'true' if this Blob is equal to the provided one.

| Parameter |         |
| --------- | ------- |
| other  | **[ref firestore.Blob]** <br /> The **Blob** to compare against.<br />Value must not be null.|

### toBase64
[methods]toBase64() returns string;[/methods]

Returns the bytes of a Blob as a Base64-encoded string.

### toUint8Array
[methods]toBase64() returns Uint8Array;[/methods]

Returns the bytes of a Blob in a new Uint8Array.
