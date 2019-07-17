# Jest

Verifies the code through simple test cases.

```javascript
import books from 'books/reducers';
import * as types from 'books/actions/types';

describe('Books reducer', () => {
   it('returns the initial state', () => {
      expect(books(undefined, {})).toEqual(
         {
            books: {}
         }
      )
   })
});
```

## More Information

* [Jest](https://jestjs.io/)

