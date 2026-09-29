Below are the current built-in React Hooks. React groups them as state, context, ref, effect, performance, and other Hooks. [Official React Hook reference](https://react.dev/reference/react/hooks)

| Hook | One-line definition | Basic syntax | Sample use case |
|---|---|---|---|
| `useState` | Stores a value that causes a re-render when updated. | `const [value, setValue] = useState(initialValue)` | Counter, input text, modal open/close state |
| `useReducer` | Manages complex state updates through a reducer function. | `const [state, dispatch] = useReducer(reducer, initialState)` | Shopping cart, multi-step form |
| `useContext` | Reads a value from the nearest matching Context provider. | `const value = useContext(MyContext)` | Theme, logged-in user, language |
| `useRef` | Stores a mutable value or DOM reference without causing a re-render. | `const ref = useRef(initialValue)` | Focus an input; store a timer ID |
| `useImperativeHandle` | Customizes the value exposed through a component ref. | `useImperativeHandle(ref, () => ({ method() {} }), [])` | Expose `focus()` from a custom input component |
| `useEffect` | Synchronizes a component with an external system after render. | `useEffect(() => { /* setup */ return () => {/* cleanup */} }, [deps])` | API connection, event listener, timer |
| `useLayoutEffect` | Runs an Effect before the browser paints the screen. | `useLayoutEffect(() => { /* measure layout */ }, [deps])` | Measure element size before showing it |
| `useInsertionEffect` | Runs before DOM changes, mainly for CSS-in-JS libraries. | `useInsertionEffect(() => { /* insert CSS */ }, [deps])` | Dynamic CSS style injection by a library |
| `useEffectEvent` | Creates non-reactive event logic that can be called inside an Effect. | `const onEvent = useEffectEvent(() => { /* latest values */ })` | Log latest cart value during a connection event |
| `useMemo` | Caches the result of a calculation between renders. | `const result = useMemo(() => calculate(data), [data])` | Filter a large product list |
| `useCallback` | Caches a function definition between renders. | `const fn = useCallback(() => { /* work */ }, [deps])` | Pass a stable callback to a memoized child |
| `useTransition` | Marks state updates as non-urgent so urgent UI stays responsive. | `const [isPending, startTransition] = useTransition()` | Update a large search-results view after typing |
| `useDeferredValue` | Delays updating a non-critical value. | `const deferredValue = useDeferredValue(value)` | Defer expensive search results while typing |
| `useId` | Generates a stable unique ID for accessibility relationships. | `const id = useId()` | Connect `<label htmlFor>` to `<input id>` |
| `useSyncExternalStore` | Subscribes React to an external data store. | `const value = useSyncExternalStore(subscribe, getSnapshot)` | Redux-like external store or browser online status |
| `useDebugValue` | Adds a label for a custom Hook in React DevTools. | `useDebugValue(value)` | Show connection status for `useOnlineStatus()` |
| `useActionState` | Manages the state and pending result of an action, often a form action. | `const [state, action, isPending] = useActionState(fn, initialState)` | Form submission status and server validation errors |

A few important notes:

- `useState`, `useEffect`, `useContext`, `useRef`, and `useMemo` are the most commonly used Hooks in regular React applications.
- `useLayoutEffect`, `useInsertionEffect`, `useImperativeHandle`, `useDebugValue`, and `useSyncExternalStore` are more specialized.
- `useCallback` is mainly useful when function identity matters—for example, when passing a callback to a `memo`-wrapped child.
- `useEffect` is for external systems such as APIs, timers, subscriptions, or browser APIs—not for normal calculations during rendering.
- All Hooks must normally be called at the top level of a React component or custom Hook—not inside `if`, loops, or event handlers.

`use` is also a React API, but it is not listed as a standard Hook because it has different rules:

```jsx
const data = use(promise);
```

It can read a Promise or Context, commonly with Suspense.