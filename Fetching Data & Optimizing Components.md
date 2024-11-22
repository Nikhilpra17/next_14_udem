#  Fetching Data on Server Side


1.  **Server-Side Data Fetching**:

-  Next.js allows fetching data directly in **server components** using async/await. This eliminates the need for useEffect, state management, or additional data-fetching libraries.

-  Data fetching happens **close to the server** and sends pre-rendered HTML to the client for faster page loads.

```ruby
async function CabinsPage() {
  const cabins = await getCabins(); // Pre-defined data-fetching function
  console.log('Starting Fetch');
  console.log(cabins);
  return <div>{cabins.map(cabin => <CabinCard key={cabin.id} cabin={cabin} />)}</div>;
}
```

----

**2\. Using the Next.js Image Component**

-  **Why Use** Image **Component**:

-  Automatic optimization: lazy loading, resizing, and format conversion.

-  Better performance compared to regular <img> tags.

-  **Setup for External Images**:

1.  Update next.config.js to allow external image hosts:
```ruby
module.exports = {
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'your-image-host.com',
        pathname: '/path-to-images/**'
      },
    ],
  },
};
```
2.	Add fill to Image components for responsiveness:
```ruby
import Image from 'next/image';

const CabinCard = ({ cabin }) => (
  <div className="relative h-48 w-full">
    <Image 
      src={cabin.imageUrl} 
      alt={cabin.name} 
      fill 
      className="object-cover"
    />
  </div>
);
```
