Agar tum chahte ho ki dynamic route ho lekin dynamic rendering ka use na ho (matlab server-side rendering ya client-side rendering use na kare), toh tum **static rendering** ka use kar sakte ho. Iske liye tum Next.js mein **`generateStaticParams`** function ka use kar sakte ho.

### Solution: Static Rendering for Dynamic Routes

1. **Step 1: Create Static Params**
   - `generateStaticParams` function ka use karo taaki tum predefined params se static pages bana sako. Isse dynamic URL ke pages build time pe hi generate ho jayenge.

2. **Step 2: Code Example**

```jsx
// app/dashboard/[id]/page.jsx

import React from 'react';

// Static params generate karenge
export async function generateStaticParams() {
  const ids = ['1', '2', '3']; // Predefined IDs

  return ids.map(id => ({ id })); // Static pages ke liye IDs return karenge
}

function Page({ params }) {
  return (
    <>
      This is the statically generated page with ID: {params.id}
    </>
  );
}

export default Page;
```

### Summary:
- Agar tum **dynamic route** ke liye **dynamic rendering** nahi chahte, to tum **`generateStaticParams`** function ka use kar sakte ho. Isse tum static pages ko build time pe generate kar sakte ho, aur baad mein koi dynamic rendering nahi hogi.

Is tarah tum apne website ka performance improve kar sakte ho kyunki pages static ho jayenge, aur har request pe server-side rendering ya client-side rendering ka load nahi hoga.


as a result of it jb npm run build kroge to aisa dikhega structure 

Route (app)                              Size     First Load JS
┌ ƒ /                                    141 B          87.2 kB
├ ○ /_not-found                          871 B          87.9 kB
└ ● /dashboard/[id]                      141 B          87.2 kB
    ├ /dashboard/1   # iska ek dynamic page bn gya . 
    ├ /dashboard/2   # iska ek dynamic page bn gya . 
    └ /dashboard/3   # iska ek dynamic page bn gya . 
+ First Load JS shared by all            87.1 kB
  ├ chunks/23-fcd997dff58d4f95.js        31.6 kB
  ├ chunks/fd9d1056-2821b0f0cabcd8bd.js  53.6 kB
  └ other shared chunks (total)          1.86 kB


○  (Static)   prerendered as static content
●  (SSG)      prerendered as static HTML (uses getStaticProps)
ƒ  (Dynamic)  server-rendered on demand

