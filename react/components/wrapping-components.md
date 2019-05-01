# Wrapping Components

```javascript
const WrapperComponent = (props) =>
   <React.Fragment>
      {props.children}
   </React.Fragment>;
```

```javascript
const MainComponent = (props) =>
   <WrapperComponent >
      Content
   </WrapperComponent >;
```



