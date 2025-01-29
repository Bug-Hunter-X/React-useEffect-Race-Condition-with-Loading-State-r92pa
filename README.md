# React useEffect Race Condition

This repository demonstrates a subtle race condition in a React component using the `useEffect` hook. The component fetches data from an API and displays a loading indicator until the data is available.  However, due to the asynchronicity of `fetch` and the timing of state updates, there's a small window where the loading indicator might not appear, even though the data hasn't loaded yet.

## Bug

The bug is in the `MyComponent` component in `bug.js`. The `setLoading(false)` is placed within the `finally` block. If the fetch is extraordinarily fast, the component might render before the loading state has time to change from true to false. 

## Solution

The solution, in `bugSolution.js`, involves updating the loading state only after the data has been successfully processed. This ensures that the loading indicator accurately reflects the component's data-fetching status.