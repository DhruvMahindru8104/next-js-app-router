### Next.js Dynamic Routes Explained in Hinglish

**Step 1: Dynamic Route Banaye**
- Tumhe `app/dashboard/[id]/page.jsx` file create karni hai. Yahaan `[id]` dynamic part hai, iska matlab URL mein jo bhi value doge, vo change ho skti hai.

**Step 2: Code likho**
- `params` object ke andar tumhare URL ka dynamic value aata hai. Agar tum `/dashboard/2` pe jaoge to `params.id === 2` hoga.

```jsx
// app/dashboard/[id]/page.jsx
import React from 'react';

function Page({ params }) {
  // params ek object hota hai, jaise { id: '100' } agar tum /dashboard/100 pe jao
  return (
    <>
      This is the dynamic route page with ID: {params.id}
    </>
  );
}

export default Page;
```

**Step 3: Main Concept**
- `{params}` ek prop hota hai jo page ko dynamic rendering ka use karne deta hai. Yeh URL ka variable part fetch karke page pe show karta hai.

### Summary:
1. **Dynamic Route**: `[id]` file name mein use karke route dynamic banate hain.
2. **`params` Object**: Isme URL ka data hota hai, jaise `{ id: '2' }` agar tum `/dashboard/2` jao.
3. **Rendering**: Page dynamically render hota hai based on URL value jo `params` se aata hai.(means jb hum `params` props ka use krte hai to vo page dynamic rendering ya server side rendering ka use krta hai )