# Notes

> Fill this in as you work. This document is assessed alongside your code.

## Bugs I found

For each: what was wrong, **why** it was wrong, and how I fixed it.

1. Products repeated API call. Whenever products state update the component rerender and useEffect run again and causing another API calling. I fixed it by changed the dependency array from *[products]* to *[]* because products only need to be fetched when component mount.

2. Products state inside useProdcut hook is using **"any[]"** event though *"Product"* type is imported. Using *"any"* removes TypeScript's type safety. So I changed the state to use the existing *"Product"* type.

3. Product search was not case-sensitive, search and category filter was not working together because of **"category !== 'All'"** condition. So I fixed it so product must match the selected **category** *AND* **search term**.

4. Hydration mismatch caused by dynamic time *Last updated at {new Date().toLocaleTimeString()}*. In Next.js, the initial HTML can be rendered on the server and then hydrated on the client. *new Date()* can return a different time between the server render and client render. I fixed it by moving the time generation into a *client-side useEffect* and stored it in state.

5. Even though *loading* is *true* but it still display the **No Products match your filters** text. This could confuse users because the products had not finished loading yet. So I fixed it by conditionally rendering the product grid based on the loading and error states.

6. The `visibleProducts` filtering logic was recalculated on every component re-render, even when the products, search term, and category had not changed. I fixed this by wrapping the calculation in `useMemo`, so it only recalculates when `products`, `search`, or `category` changes. This avoids unnecessary filtering during unrelated re-renders.

## Features I completed

- Render the error state when request fails.
- 

## Decisions

Anywhere I had to choose between options — and why I chose what I did.

-

## With more time

What I'd improve or add next.

-
