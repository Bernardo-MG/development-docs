# Dynamic Construction

```jsx
function NumberList(props) {
   const numbers = props.numbers;
   return (
      <ul>
         {numbers.map((number) =>
         <ListItem key={number.toString()} value={number} />
         )}
      </ul>
   );
}
```

Note the 'key' attribute. This should be unique among the created nodes, and is required.

