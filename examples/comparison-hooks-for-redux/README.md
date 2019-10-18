# Comparison-Hooks-For-Redux

This example is one of two comparing hooks-for-redux with vanilla redux in a very simple app.

## Compare

* comparison-vanilla-redux
* comparison-hooks-for-redux

## JavaScript Source

With hooks-for-redux, you have to write dramatically less code. Here's all the JavaScript source in one place:

```jsx
// greetingReduxState.js
import { useReduxState } from 'hooks-for-redux'

const DEFAULT_GREETING = "hello, hooks-for-redux!";

const [useGreetingSubscription, /*updateGreeting*/, addReducers] =
  useReduxState('greeting', DEFAULT_GREETING);

const {resetGreeting, setGreeting} = addReducers({
  resetGreeting: () => DEFAULT_GREETING,
  setGreeting: (store, greeting) => greeting
})

export {useGreetingSubscription, resetGreeting, setGreeting}

// App.js
import React from 'react'
import {useGreetingSubscription, setGreeting, resetGreeting}
  from './greetingReduxState'

const App = () =>
  <div>
    <h1>{ useGreetingSubscription() }</h1>
    <a href="#" onClick={() => setGreeting("こんにちは, hooks-for-redux")}>
      japanese
    </a> <a href="#" onClick={() => resetGreeting()}>reset</a>
  </div>

export default App

// index.js
import React from 'react'
import ReactDOM from 'react-dom'
import {Provider} from 'hooks-for-redux'
import './index.css'
import App from './App'

ReactDOM.render(<Provider><App/></Provider>, document.getElementById('root'));

```