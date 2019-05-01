# Components

Simple components can be declared as functions:

```javascript
const CustomComponent = (props) =>
   <div>
      This is a component
   </div>;
```

They can be declared also as classes, which is more useful for complex components with internal state or custom operations:

```javascript
class CustomComponent extends Component {
   render() {
      <div>
         This is a component
      </div>
   }
}
```

