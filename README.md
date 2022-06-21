# pinia-system-messages-store

A store definition that helps you to organize your system messages. You can create a component in your application that shows system messages on the UI and you can use the actions all over your app to show error messages, warnings, info and success messages.

Usage:

First, create your store.
```javascript
// (stores/systemMessages.js)
import pinia from 'pinia'
import systemMessages from 'pinia-system-messages-store'

export default defineStore('systemMessages', systemMessages)
```

Somewhere else in your code:
```javascript
import systemMessages from './systemMessages.js'

...

useSystemMessages().addError({ status: 404, name: 'NOT_FOUND', message: 'The entry you are searching for is not found.' })

...
```


State:
 - items []

Each item is an object with the following properties:
 - type: the type of the system message ('error', 'warning', 'info', 'success')
 - state: the current state of the system message ('fading-in', 'fully-visible', 'fading-out')
 - name: the name of the system message
 - status: an optional property to show HTTP status codes
 - message: the message to show to the user

Actions:
 - addError({ status, name, message }, { fullyVisibleAfter = 250, fadingOurAfter = 4750, removeAfter = 5000 } = {})
 - addWarning({ status, name, message }, { fullyVisibleAfter = 250, fadingOurAfter = 4750, removeAfter = 5000 } = {})
 - addInfo({ status, name, message }, { fullyVisibleAfter = 250, fadingOurAfter = 4750, removeAfter = 5000 } = {})
 - addSuccess({ status, name, message }, { fullyVisibleAfter = 250, fadingOurAfter = 4750, removeAfter = 5000 } = {})