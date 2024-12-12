# React 19 useEffect Runs Twice on Initial Render

This repository demonstrates a subtle bug in React 19 where a `useEffect` hook runs twice on the initial render. This can lead to unexpected behavior and console spam, making it challenging to debug.  The issue is particularly noticeable when the effect involves side effects such as API calls or logging.

## Bug Description

A `useEffect` hook with an empty dependency array should only run once after the initial render. However, in this example (and others reported with React 19), the effect runs twice.  The first run is expected, but the second is unexpected and often problematic.

## Reproduction Steps

1. Clone this repository.
2. Run `npm install`.
3. Run `npm start`.
4. Observe the console. You'll see that the message 'Count changed:' is logged twice on the initial render.

## Solution

The solution is to ensure that there are no unnecessary state updates or re-renders happening within the component before `useEffect` is called. A common solution to preventing this is ensuring that the effect is only called on component mount and not re-rendered unnecessarily.