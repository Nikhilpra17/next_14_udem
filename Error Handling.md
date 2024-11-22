**Step-by-Step Guide to Setting Up a Global Error Boundary**

1.  **When Errors Occur:**

-  Invalid IDs (e.g., bookmarked outdated URLs) result in rendering errors like null values in destructuring.

-  Incorrect assumptions in code (e.g., accessing capacity.max instead of capacity) may lead to runtime errors.

-  **Development Mode vs. Production Mode**: Development shows detailed errors; production hides technical details.

2.  **Creating** Error.js**:**

-  Place the file in the root app/ directory.

-  Use the following code structure:

```ruby
'use client';

export default function Error({ error, reset }) {
  return (
    <div>
      <h1>Something Went Wrong</h1>
      <p>{error.message}</p>
      <button onClick={reset}>Try Again</button>
    </div>
  );
}
```

3.  **Understanding the Code:**

-  error: Captures the error object.

-  reset: Function to reset the error boundary.

4.  **Error Display in the UI:**

-  Replace generic messages with error.message for detailed feedback (useful for developers).

-  Ensure the error page matches the application's overall styling.

5.  **Using Nested Error Boundaries:**

-  Next.js allows multiple Error.js files at different levels of the application.

-  The **closest boundary** catches the error.

-  Only rendering errors (not callback function errors) are caught.

---

**Limitations of Error.js:**

-  **Root Layout Errors:**

Errors in root layout (e.g., during data fetching) are not caught by Error.js.

-  **Solution:**

-  Use global-error.js to handle such cases.

-  Example structure:

```ruby
'use client';

export default function GlobalError({ error, reset }) {
  return (
    <html>
      <body>
        <h1>Critical Error</h1>
        <p>{error.message}</p>
        <button onClick={reset}>Reload</button>
      </body>
    </html>
  );
}
```

---

**Step-by-Step Guide to Implement Not Found Errors in Next.js:**

**1\. Default 404 Page Replacement**

-  Create a not-found.js file in the app directory:

```ruby
// app/not-found.js
import Link from "next/link";

export default function NotFound() {
    return (
        <div style={{ textAlign: "center" }}>
            <h1>This page could not be found</h1>
            <Link href="/">Go back to the homepage</Link>
        </div>
    );
}
```
-  Automatically displayed when:

-  The user navigates to a route that doesn't exist.

-  **Result**: A custom-styled 404 page replacing the default Next.js error screen.

**2\. Manually Triggering a Not Found Error**

-  Use the notFound function from next/navigation to programmatically display the 404 page.

-  Example:

```ruby
import { notFound } from "next/navigation";

async function getCabin(id) {
    const cabin = await fetchCabinById(id); // Your data fetching logic
    if (!cabin) {
        notFound(); // Triggers the 404 page
    }
    return cabin;
}
```
