# Conditional Rendering

## Element Variable

```javascript
function DividedComponent ({ divide }) {
   let divider;

   if(divide) {
      divider = <Divider />;
   }

   return <React.Fragment>
      <Component />
      {divider}
   </React.Fragment>;
}
```

