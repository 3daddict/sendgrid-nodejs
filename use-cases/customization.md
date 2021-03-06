# Customization Per Recipient

To send multiple individual emails to multiple recipients with additional customization (like a different subject), use the `personalizations` field as per the [API definition](https://sendgrid.com/docs/API_Reference/api_v3.html) instead of `to`, leveraging all customization options:

```js
const msg = {
  personalizations: [
    {
      to: 'recipient1@example.org',
      subject: 'Hello recipient 1',
      substitutions: {
        name: 'Recipient 1',
        id: '123',
      },
      headers: {
        'X-Custom-Header': 'Recipient 1',
      },
      customArgs: {
        myArg: 'Recipient 1',
      },
    },
    {
      to: 'recipient2@example.org',
      subject: 'Hello recipient 2',
      substitutions: {
        name: 'Recipient 2',
        id: '456',
      },
      headers: {
        'X-Custom-Header': 'Recipient 2',
      },
      customArgs: {
        myArg: 'Recipient 1',
      },
      sendAt: 1500077141,
    }
  ],
  from: 'sender@example.org',
  text: 'Hello plain world!',
  html: '<p>Hello HTML world!</p>',
};
```

If the `substitutions` field is provided globally as well, these substitutions will be merged with any custom substitutions you provide in the `personalizations`.
