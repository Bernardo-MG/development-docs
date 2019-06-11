# Jest

Allows running tests on Javascript objects, including React components:

```javascript
describe('<ButtonInput />', () => {
   it('handles button click when there is a value', () => {
      const { wrapper, props } = setup();
      const textField = wrapper.find(TextField);
      const button = wrapper.find(Button);

      textField.props().onChange({ target: { value: 'abc' } });
      button.simulate('click', {type: 'click'});
      expect(props.action.mock.calls.length).toBe(1);
   })
})
```

