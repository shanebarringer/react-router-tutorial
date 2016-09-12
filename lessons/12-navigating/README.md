# Navigating Programatically

While most navigation happens with `Link`, you can programmatically
navigate around an application in response to form submissions, button
clicks, etc.

Let's make a little form in `Repos` that programmatically navigates.

### Challenge
- Add the following `handleSubmit` method to your `Repos` Component:

```javascript
// modules/Repos.js
import React from 'react'
import NavLink from './NavLink'

export default class Repos extends React.Component {

  // add this method
  handleSubmit(event) {
    event.preventDefault()
    const userName = event.target.elements[0].value
    const repo = event.target.elements[1].value
    const path = `/repos/${userName}/${repo}`
    console.log(path)
  }

  //...

}
```

- Create a form component in your render method
  - Nest the form inside of a list item component (in your `<ul>`)
  - in your form component, pass the `handleSubmit` function to an `onSubmit` attribute
  - Create the following components (inside your form):
    - `<input type="text" placeholder="userName"/> / {' '}`
    - `<input type="text" placeholder="repo"/>{' '}`
  - Add a button component and close out your form



There are two ways you can do this, the first is simpler than the
second.

First we can use the `browserHistory` singleton that we passed into
`Router` in `index.js` and push a new URL into the history.

```javascript
// modules/Repos.js
import { browserHistory } from 'react-router'

// ...
  handleSubmit(event) {
    // ...
    const path = `/repos/${userName}/${repo}`
    browserHistory.push(path)
  }
// ...
```

There's a potential problem with this though. If you pass a different
history to `Router` than you use here, it won't work. It's not very
common to use anything other than `browserHistory`, so this is
acceptable practice. If you're concerned about it, you can make a module
that exports the history you want to use across the app, or...

You can also use the `router` that `Router` provides on "context".

First, you assign `contextTypes` to your component

```javascript
export default class Repos extends React.Component {
  // ...

}

Repos.contextTypes = {
    router: React.PropTypes.object
}
```

Second, in your constructor function

- pass context as the second argument
- access the router option (belonging to context): `context.router`

```javascript
export default class Repos extends React.Component {
  constructor(props, context){
    super(props)
    context.router
  }

  // ...

  handleSubmit(event) {
    // ...
    this.context.router.push(path)
  },

  // ..
}

Repos.contextTypes = {
    router: React.PropTypes.object
}
```

This way you'll be sure to be pushing to whatever history gets passed to
`Router`. It also makes testing a bit easier since you can more easily
stub context than singletons.

---

[Next: Server Rendering](../13-server-rendering/)
