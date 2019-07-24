## exc 1
reducer(previousState, dispatchArg){
  return newState
}

there might be a third arg for lazy initialization, then:
const [count, setCount] = React.useReducer(countReducer, initialCount, lazyInit)

function lazyInit(initialCount) {
  return Number(window.localStorage.getItem('count') || initialCount)
}
-> so lazy init would take data from localStorage OR resort to initial count

### extra 2
objects as arguments:

function countReducer(state, newState){
  return {...state, ...newState}
}

-------------------
function countReducer(state, newState){
  return {...state,
    ...(typeof newState === 'function' ? newState(state) : newState)
  }}

### extra 3
hack in switches:

default: {
  throw Error(`type not supported: ${action.type}`)
}

useReducer when you have a few elements of state that all relate to each other and change together or when you have some complex state update and its logic will live inside a component (e.g. function) then you can take it out somewhere else

Redux you can put all the state in one place -> mistake
it's easier to maintain the code when the state lives right there; you don't need to serialize it to local storage; you can use context to do that

by the way, you can use multiple redux stores! :O

## exc 2
Kent advises to destructure the state

nested states: immer package -> it mutates the immutable state

useEffect happens after the render, when changed
async callbacks are different are different each time because it's a closure

if we don't provide dependencies, useEffect will hit dispatch that will re-render because it's a promise i.e. different object every time; providing the empty array at the end prevents that;

redux has unstable API
react hooks (context + useReducer) has stable api
react useMemo prevents unnecessary rerenders

### useCallback vs useMemo
read the blog post!

useCallback is built on top of useMemo
if overused, the app will get slower

## exc 3
pay attention to that only usage is exported

hooks provide nicer experience for the user than renderprops + it's easier to use Hooks

Kent hates recompose because every time he sees a code with it, he doesn't know what's going on

testing with context with so many layers of providers:
render (<CountProvider>
<CountDisplay />
</CountProvider>)
and overriding the value: <CountProvider value={5}>

## exc 5
useLayoutEffect looks pretty
if your effect is making observable changes to the DOM then useLayoutEffect, otherwise useEffect
useLayoutEffect is longer

## exc 6
useImperativeHandle has useLayoutEffect under the hood

## exc 7
if you're using hooks that use hooks

## Questions:
- redux middleware
- react context / context providers
- immutable state
- lodash
- deep copy
- async functions
- async callbacks
- useAsync
- memoization
- "dependencies are stable"
- referential equality
- caching
- React.lazy(loader)
- children prop
- event bubbling
- HoC
- HoC vs renderprops
- recompose
- shallow rendering (jest mock <- ? to render without children)
- side-effects
- afterBrowserPaints
- cleanupPreviousEffects
- useImperativeHandle
- refs (e.g. .forwardRef)
- formatter function



## Read more
- useReducer vs useState blog post by Wieruch
- colocation blog post by Kent C. Dodds
- Application State Management with React by Kent C. Dodds
- bookshelf repo by Kent C. Dodds
- useCallback vs useMemo by Kent C. Dodds
- Application State Management
- lifting State UP -> docs https://reactjs.org/docs/lifting-state-up.html
- '@reach/router'
- import {createBrowserHistory} from 'history'
- never write another HoC Michael Jackson (Kent uses css not HoCs)
- React Hooks: What's going to happen to render props? by Kent C. Dodds
- testing-library.com
- why I never use shallow rendering by Kent
- how to use React Context effectively
- look at instapaper.com or app.getpocket.com
- [Imperative vs Declarative Programming](https://tylermcginnis.com/imperative-vs-declarative-programming/)

-------------------------------
CODEBUDDIES!!!!!!!!!!!

https://spectrum.chat/kentcdodds

testing javascript with Kent
