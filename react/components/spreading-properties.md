# Spreading Properties

Sometimes passing properties from a higher order component to the one it wraps feels redundant:

```jsx
const BookSearchForm = (props) => <ButtonInput
   id={props.id}
   label={props.label}
   buttonLabel={props.buttonLabel}
   action={props.search}
/>;
```

This can be resolved by using the spread operator, which will send those properties, matching keys, to the wrapped component:

```jsx
function BookSearchForm(props) { return <ButtonInput {...props} />; }
```

