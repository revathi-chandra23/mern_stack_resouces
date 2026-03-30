## what is virtual DOM?

- the virtual DOM is lightweight JS representation of the real dom.
  React uses it to improve performance by making update more efficient.

## How many virtual DOMs does react have ?

- react has two virtual DOM.
  - one for the previous state.
  - one for the new state.
- it compares these two using a process calling diffing to determine the changes and update the real DOM.

## what is the difference between class base component and functional based component ?

- class Components
  - ES6 classes
  - Have lifecycle methods like componentDidMount(), componentDidUpdate(), componentWillUnmount
  - requires this for accessing states and props.
- function components
  - a simpler , just javascript functions..
  - use Hooks( eg, useState, useEffect)for state and props.
  - easer to read and maintain.

## what hooks do you use in react ?

- useState for managing state
- useEffect for side effects like api calls, setTimeout.
- useRef- to access dom elements directly, to reduce unnecessary re-render.
- useReducer- it is used for complex state logic (more than two states)
- useContext -it is used to access data from a React context without manually passing props through each component.
- useQuery -to reduce unnecessary api calls ( by caching the data)
- useParam- to access queryparams from the url (?q="flm")
- useNavigate - it is used to navigate the user from one page to another without user interaction
- useMemo - it is used for performance optimizing technique, here the result value will be stored inside useMemo ( useMemo(calcuation, dependency))
- useCallback - it is used as optimizing technique

## what is jsx in react ?

it means javascript xml,
it allows developers to write html-like code in javascript, which is then transformed into react element using babel.

## can jsx be directly understood by the browser ?

no , the browser cannot understand jsx, it needs t be transpiled into regular javascript using tools like babel before being renders.

## what are props in react ?

Props (properties) is used to pass data from parent component to a child component. It enables components reusability

## how are props different from state ?

- props - passed from parent to child and read-only.
- state- manged within the components and can change over time.

## why are keys important in react lists ?

## what are the options for state management in react ?

- local state
  - useState
  - useReduce
- global state
  - context api
- libraries ( global state)
  - Redux.

## what is react StrictMode ?

## what are higher order component ?

## what are the core concepts or redux?

store, action, reducer, dispatch, middleware

## what is link and Navlink in react router?

## what is difference b/w css modules and styled component

### javascript

- How does map method works in javascript ?
- what is event.prevent.default ?
- what is debouncing and how is it implemented ?

`const debounce = (func, delay) {
    let timerId;
    return (...args)=>{
        clearTimeout(timerId);
        timerId= setTimeout(()=>func(...args),delay)
    }
}
const search= debounce((query)=>console.log(query),300);`
