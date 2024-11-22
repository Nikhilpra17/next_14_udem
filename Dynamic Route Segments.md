
1.  **Dynamic Route Segments**:

-  URLs such as /cabins/91 or /cabins/89 have parts (e.g., the ID) that are unknown at build time.

-  Instead of creating separate folders for each ID, we use **dynamic segments**.

2.  **Creating Dynamic Routes**:

-  Inside the cabins folder, create a **dynamic route folder**:
  ```ruby
/cabins/[cabinId]/Page.js
```

-  Use **square brackets** ([ ]) to define the dynamic segment. The name inside brackets (cabinId) becomes the **key** for accessing the dynamic part of the URL.

3.  **Dynamic Page Implementation**:

-  Add a Page.js file inside the [cabinId] folder.

-  Fetch the cabin data dynamically using the dynamic segment.

```ruby
export default async function Page({ params }) {
  console.log(params); // { cabinId: "91" }
  const cabin = await getCabin(params.cabinId);
  return <div>{cabin.name}</div>;
}
```

----

***Dynamic Metadata***

1.  **Static vs. Dynamic Metadata:**

-  By default, page metadata (like titles) is static in Next.js. However, in dynamic pages, metadata like the title should adapt to the specific content (e.g., cabin names).

2.  **Dynamic Metadata Generation:**

-  Next.js provides a generateMetadata function to fetch dynamic data and update metadata, such as the **title**.


```ruby
export async function generateMetadata({ params }) {
    // Fetch cabin data dynamically using cabin ID
    const cabin = await getCabin(params.cabinId);
    
    // Destructure the cabin name
    const { name } = cabin;

    // Return metadata object
    return {
        title: `Cabin ${name}`, // Dynamic title
    };
}
```
