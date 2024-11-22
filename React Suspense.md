# What is React Suspense?

-  **React Suspense** is a built-in React component that helps manage asynchronous rendering.

-  It "catches" components (or subtrees) that are not ready to be rendered due to pending asynchronous operations (e.g., data fetching or lazy loading code).

---

**Key Concepts**

1.  **Suspending Components**:

-  A component is said to "suspend" when it performs an asynchronous operation and is not yet ready to render.

-  Suspense works like a try-catch block but catches suspending components instead of errors.

2.  **Main Use Cases**:

-  **Data fetching** using libraries that support Suspense (e.g., React Query, Next.js).

-  **Lazy loading** additional code with React.lazy.

3.  **Fallback UI**:

-  Suspense shows a fallback (e.g., a spinner) while the asynchronous operation completes.

-  This eliminates the need for manually managing loading states in components.

---

**Implementation Steps:**

1.  **Create a New Component**:

-  Extract the data-fetching and rendering logic for the cabin list into a new component (CabinList.js).

2.  **Make the Component Async**:

-  Since CabinList handles data fetching, define it as an async component.

3.  **Wrap in Suspense**:

-  Use React's Suspense to wrap the CabinList component, specifying a fallback JSX element (e.g., <Spinner />) to display while waiting for data.
