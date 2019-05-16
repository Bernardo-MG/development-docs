# Internationalization

The [react-intl](https://github.com/formatjs/react-intl) project allows internationalizating react apps.

## Apply to Component

```jsx
import { injectIntl } from 'react-intl';
import messages 'i18n/messages';

const InternationalizedComponent = () =>
   <div>props.intl.formatMessage(messages.text)}</div>

InternationalizedComponent .propTypes = {
   intl: intlShape.isRequired
};

export default injectIntl(InternationalizedComponent );
```

## Internationalization Messages

```jsx
import { defineMessages } from 'react-intl';

const messages = defineMessages({
   search: {
      id: 'messages.text',
      defaultMessage: 'Text'
   }
});

export default messages ;
```

## Initialize App

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import {addLocaleData, IntlProvider} from 'react-intl';
import enLocaleData from 'react-intl/locale-data/en';
import App from '/components/app';

addLocaleData(enLocaleData);

const {locale, messages} = window.App;

ReactDOM.render(
    <IntlProvider
        locale={locale}
        messages={messages.app}
    >
        <App />
    </IntlProvider>,
    document.getElementById('container')
);
```

