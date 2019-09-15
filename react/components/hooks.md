# Hooks

## State Hook

Handles components state.

```javascript
const [count, setCount] = useState(0);
```

## Effect Hook

Runs after the DOM is changed.

```javascript
useEffect(() => {
   // Update the document title using the browser API
   document.title = `You clicked ${count} times`;
});
```

## More Information

* [Introducing Hooks](https://reactjs.org/docs/hooks-intro.html)

