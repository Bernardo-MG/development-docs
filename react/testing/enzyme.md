# Enzyme

Verifies React Components.

## Snapshots

The easiest way to use Enzyme is by generating UI snapshots from components. This will verify that the generated code does not change over time.

```javascript
import React from 'react'
import renderer from 'react-test-renderer';

import ButtonInput from 'common/components/ButtonInput';

describe('<ButtonInput />', () => {
   it('renders correctly', () => {
      const tree = renderer
         .create(<ButtonInput
               id='testButtonInput'
               label='label'
               buttonLabel='button label'
               action={ () => 'action' } />)
         .toJSON();
      expect(tree).toMatchSnapshot();
   })
});
```

## Interaction

It allows testing user interaction with the component too.

```javascript
import React from 'react'
import { shallow, configure } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16';

import ButtonInput from 'common/components/ButtonInput';

import Button from '@material-ui/core/Button';
import TextField from '@material-ui/core/TextField';

configure({ adapter: new Adapter() });

function setup() {
   const props = {
      id: 'id',
      label: 'label',
      buttonLabel: 'buttonLabel',
      action: jest.fn()
   }

   const wrapper = shallow(<ButtonInput {...props} />)

   return {
      props,
      wrapper
   }
}

describe('<ButtonInput />', () => {
   it('ignores button click on empty text', () => {
      const { wrapper, props } = setup();
      const textField = wrapper.find(TextField);
      const button = wrapper.find(Button);

      textField.props().onChange({ target: { value: '' } });
      button.simulate('click', {type: 'click'});
      expect(props.action.mock.calls.length).toBe(0);
   })
})
```

