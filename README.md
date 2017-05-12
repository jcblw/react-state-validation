# React State Validation

[![Greenkeeper badge](https://badges.greenkeeper.io/jcblw/react-state-validation.svg)](https://greenkeeper.io/)

[![Build Status](https://travis-ci.org/jcblw/react-state-validation.svg)](https://travis-ci.org/jcblw/react-state-validation)

React State Validation uses the propTypes validation pattern to validate states.

## Usage

The `stateValidation` method can be used a decorator.

```javascript
import React, {Component} from 'react'
import {stateValidation} from 'react-state-validation'
const stateValidations = {
  customState: function(state, stateName, componentName) {
    if (!/matchme/.test(state[stateName])) {
      return new Error('Validation failed!');
    }
  }
}


@stateValidation
class App extends Component {
  constructor () {
    super()
    this.state = {
      customState: ''
    }
  }

  render () {
    // the stateValidation method will set the errors key will the current state errors
    const {errors} = this.state
    // the key of the state will be the same key in the errors object
    const {customState} = errors
    // if there is errors it will be an array of strings
    // eg. ['Validation failed!']
    //...
  }
}

App.stateValidations = stateValidations
```

or if your not using decorators you can just wrap the component with the stateValidation method.

```javascript
export stateValidation(App)
```

## Contributing

Plz do it! oh and run `npm test`. I use [standard](http://standardjs.com/) for code style/linting, and [ava](https://github.com/sindresorhus/ava) for testing.


## Cool modules to use with this

- [react-validator-prop-types](https://www.npmjs.com/package/react-validator-prop-types)
