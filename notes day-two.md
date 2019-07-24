### exc 1
reducer(previousState, dispatchArg){
  return newState
}

there might be a third arg for lazy initialization, then:
const [count, setCount] = React.useReducer(countReducer, initialCount, lazyInit)

function lazyInit(initialCount) {
  return Number(window.localStorage.getItem('count') || initialCount)
}
-> so lazy init would take data from localStorage OR resort to initial count


### Questions:

### Read more
