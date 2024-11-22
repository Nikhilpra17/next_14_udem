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
