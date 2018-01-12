# FieldPath

```
firebase.firestore.FieldPath
```

### FieldPath
[method]new FieldPath(...var_args);[/method]

A FieldPath refers to a field in a document. The path may consist of a single field name (referring to a top-level field in the document), or a list of field names (referring to a nested field in the document).

Create a FieldPath by providing field names. If more than one field name is provided, the path will point to a nested field in a document.

| Parameter |         |
| --------- | ------- |
| var_args  | A list of field names. <br /> Value may be repeated. |

## Methods

### documentId
[methods]documentId() returns [ref firestore.FieldPath];[/methods]

Returns a special sentinel `FieldPath` to refer to the ID of a document. It can be used in queries to sort or filter by the document ID.
