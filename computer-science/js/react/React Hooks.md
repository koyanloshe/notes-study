# React Hooks

Can be used only with functional components and not will class-based components

# Basic Hooks

* useState
* useEffect
* useContext

## useState

`import { useState } from ‘react’`
`const [state, setState] = useState(initialState)`

This replaces this.state and this.setState()

## useEffect

`import { useEffect } from 'react'`
`useEffect(didUpdate)`

This replaces componentDidMount, componentDidUpdate and componentWillUnmount methods.

The effect hook allows for returning a cleanup function from it which works similarly to adding a function to componentWillUnmount

## useContext

`import { useContext } from ‘react’`
`const value = useContext(myContext)`

It replaces context consumers.

# Additional Hooks

* useRef
* useReducer
* useMemo
* useCallback
* useLayoutEffect
* useDebugValue

## useRef

`import { useRef } from ‘react’`
`const refContainer = useRef(initialValue)`

The useRef hook is used to deal with references to elements and components in React. We can set a reference by passing the ref prop to an element or a component as below:
`<ComponentName ref={refContainer} />`

## useReducer

`import { useReducer } from ‘react’`
`const [state, dispatch] = useReducer(reducer, initialArg, init)`

The useReducer hook is used to deal with complex state logic

## useMemo

Memoization is an optimisation technique where the result of a function Is cached and is then returned when the same input occurs again. This hook allows a compute and memoize.

`import { useMemo } from ‘react’`
`const memoizedValue = useMemo(() => computeExpensiveValue(a,b), [a, b])`

## useCallback

`import { useCallback } from 'react'`
`const memoizedCallback = useCallback(`
`    () => {  `
`        doSomething(a, b)`
`    },`
`    [a, b]`
`)`

This is useful when passing callbacks to optimised child components. It works similarly to the useMemo hook but for callback functions.

## useLayoutEffect

`import { useLayoutEffect } from 'react'`
`useLayoutEffect(didUpdate)`

Similar to useEffect but only fires after all DOM mutations are complete.
It can be use to read info from the DOM

## useDebugValue

`import { useDebugValue } from 'react'`
`useDebugValue(value)`

This is used to make it easier to debug hooks

# Community Hooks

useInput
useResource
useDimensions
Navigation Hooks
Lifecycle Hooks
Timer Hooks

## useInput

`import { useInput } from 'react-hookedup'`
`function App () {    `
`	const { value, onChange } = useInput('')       `
`	 return <input value={value} onChange={onChange} />`
`}`

## useResource

`import { useRequest } from 'react-request-hook'`
`const [profile, getProfile] = useResource(id => ({`
`    url: `/user/${id}`,`
`    method: 'GET'`
`})`

This is used to simplify fetching data

## Navigation Hooks

`import { useCurrentRoute, useNavigation } from 'react-navi'`
`const { views, url, data, status } = useCurrentRoute()`
`const { navigate } = useNavigation()`

Hooks make routing much easier to deal with

## Life Cycle Hooks

`import { useOnMount, useOnUnmount } from 'react-hookedup'`
`useOnMount(() => { ... })`
`useOnUnmount(() => { ... })`

Hooks can directly replace life-cycle methods in class components

## Timer Hooks

`import { useInterval, useTimeout } from 'react-hookedup'`
`useInterval(() => { ... }, 1000)`
`useTimeout(() => { ... }, 1000)`

Hooks greatly simplify how we deal with intervals and timeouts in React

