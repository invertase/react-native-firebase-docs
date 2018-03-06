# Cloud Firestore Transactions

A transaction is a set of read and write operations on one or more Cloud Firestore documents that execute in a single atomic operation - either all of the operations succeed, or none of them are applied.

Transactions are useful when you want to update a field's value based on it's current value or the value of some other field. For example you could increment a counter by creating a transaction that reads the current value of the counter, increments it, and writes the new value to Cloud Firestore.

A transaction can consist of any number of `get()` operations followed by any number of write operations using methods such as `set()`, `update()` and `delete()`.

## Caveats

When using transactions the following points should be kept in mind:

- **Transactions** will **fail** when the client is **offline**.
- **Read** operations are **asynchronous** (Promises).
- **Read** operations must come **before write** operations.
- Your **updateFunction** **can return** a **Promise**.
- **Write** operations are **synchronous** but don't apply until after your `updateFunction` has finished executing.
- Your transaction `updateFunction` might run more than once if a concurrent edit affects a document that the transaction reads.
- Transaction `updateFunction` should not directly modify react state, you'd do this in the result of the transaction.

## Examples

### Increment a value transactionally

```javascript
import { firestore } from 'react-native-firebase';

const ref = firestore.collection('cities').doc('London');

firestore
  .runTransaction(async transaction => {
      const doc = await transaction.get(ref);
      
      // if it does not exist set the population to one
      if (!doc.exists) {
          transaction.set(ref, { population: 1 });          
          // return the new value so we know what the new population is
          return 1;
      }
      
      // exists already so lets increment it + 1      
      const newPopulation = doc.data().population + 1;
      
      transaction.update(ref, {
          population: newPopulation,
      });
      
      // return the new value so we know what the new population is
      return newPopulation;      
  })
  .then((newPopulation) => {
      console.log(`Transaction successfully committed and new population is '${newPopulation}'.`);
  })
  .catch((error) => {
      console.log('Transaction failed: ', error);
  });
```
