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

## useCallback vs useMemo
read the blog post!

useCallback is built on top of useMemo
if overused, the app will get slower

useMemo


## Questions:
- redux middleware
- react context
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

## Read more
- useReducer vs useState blog post by Wieruch
- colocation blog post by Kent C. Dodds
- Application State Management with React by Kent C. Dodds
- bookshelf repo by Kent C. Dodds
- useCallback vs useMemo by Kent C. Dodds
