System Design

How would you structure a large-scale React application to ensure maintainability and scalability?

एक folder स्ट्रक्चर बनाना होता है जिससे separation of concerns रहता है, मतलब फाइल्स segregated रहती है। 
Atomic Design होना चाहिए मतलब कंपोनेंट्स को जितना हो सके उतना छोटे टुकड़ों मैं तोड़ के रखना। buttons, input बॉक्स अलग, forms, cards एकसाथ वगैरह।  
हर component अपनी styles, tests, और logic खुद मैनेज करे अलग फोल्डर मैं.
State Management मैं Local स्टेट के लिए useState या useReducer use हो, Global के लिए Context API या Redux use हो और Server स्टेट के लिए React Query , SWR वगैरह.
Use React Router for navigation.
Use lazy loading and dynamic imports (React.lazy()).
Optimize re-renders with useMemo, useCallback, and React.memo.
Enable server-side rendering (SSR) or static site generation (SSG) for Next.js.
Linting & Formatting: Use ESLint, Prettier, Husky (for pre-commit hooks).
Testing: Use Jest, React Testing Library, Cypress for unit/integration/e2e testing.
CI/CD: Automate deployments using GitHub Actions, Vercel, or Netlify.
Store sensitive data in .env files.
Secure API calls with auth tokens and refresh mechanisms.
Prevent XSS attacks by sanitizing user input.

* SWR मतलब stale-while-revalidate, इसमें पहले data cache (stale) से return होता है फिर API request send होती है और फिर finally up-to-date data आता है




Q. What are the best practices for organizing components, state management, and API calls in a React app?

A . For a well-structured React app, use a feature-based folder structure to keep components modular and reusable. Manage local state with useState or useReducer, global state with Redux Toolkit or Zustand, and server state with React Query for caching and syncing. Centralize API calls in a services/ folder and use Axios with interceptors. Optimize performance with memoization, virtualization, and lazy loading. Ensure reliability with unit, integration, and E2E tests, and secure data with JWT, CORS, and Helmet. This keeps the app scalable, maintainable, and performant. 🚀




Q. How do you decide between using local component state, Context API, or a state management library like Redux or Zustand?
A. Choose based on state scope and frequency of updates:
Local State (useState, useReducer) – Best for UI-related, ephemeral state like modals, forms, and toggles.
Context API – Ideal for low-frequency global state like themes, authentication, and user preferences. Avoid for frequently changing data to prevent re-renders.
Redux Toolkit / Zustand – Use for complex global state like user sessions, API caching, or shared data across many components. Redux is structured and scalable, while Zustand is simpler and more lightweight.




Q. How would you optimize the performance of a React/Next.js application?
A. To optimize React/Next.js performance:
Code Splitting & Lazy Loading – Use React.lazy, Suspense, and dynamic imports to load components only when needed.
Memoization – Use useMemo and useCallback to prevent unnecessary re-renders.
Virtualization – Use react-window or react-virtualized for rendering large lists efficiently.
Image Optimization – Use Next.js next/image for automatic resizing and lazy loading.
Server-Side Rendering (SSR) & Static Site Generation (SSG) – Use SSR for dynamic content (getServerSideProps) and SSG (getStaticProps) for static pages.
Reduce Unnecessary Renders – Use React.memo and optimize state updates.
Optimize API Calls – Use React Query or SWR for caching and background data fetching.
These techniques improve speed, responsiveness, and efficiency. 🚀





Q. What strategies would you use to reduce bundle size and improve load times?
A. To reduce bundle size and improve load times:
Code Splitting & Lazy Loading – Use React.lazy and dynamic() in Next.js to load components only when needed.
Tree Shaking – Ensure Webpack removes unused code by using ES modules (import { specificFunction } from 'library').
Optimize Dependencies – Replace heavy libraries with lighter alternatives (e.g., lodash-es instead of lodash).
Image & Asset Optimization – Use Next.js next/image for automatic compression and lazy loading.
Minification & Compression – Enable Gzip or Brotli compression on the server.
Remove Unused Code – Analyze with Webpack Bundle Analyzer and remove unnecessary imports.
Self-host Fonts & Icons – Use system fonts or locally hosted fonts instead of external CDNs.
These strategies ensure a faster, more efficient app. 🚀





Q. How do you handle lazy loading of components and routes in React/Next.js?
A. Lazy loading is a technique that delays loading non-essential components or routes until they are needed, improving initial load times and performance.
In React, React.lazy() and Suspense allow components to load dynamically, reducing the initial bundle size.
In Next.js, next/dynamic() enables SSR-aware lazy loading, ensuring components load only on the client when required.
For routes, code splitting ensures only the necessary pages load, reducing unused JavaScript execution.
By implementing lazy loading, apps improve speed, reduce memory usage, and enhance user experience by prioritizing critical content first. 🚀




Q. When would you choose SSR over SSG in a Next.js application?
A. Choose SSR (Server-Side Rendering) when data needs to be fresh on every request, such as:
Personalized Content (e.g., user dashboards, authenticated pages).
Frequently Changing Data (e.g., live stock prices, real-time news).
SEO-Optimized Dynamic Pages (e.g., product pages with frequently updated prices).
Choose SSG (Static Site Generation) when data can be pre-built at build time, such as:
Blog Posts, Marketing Pages, Documentation (rarely updated content).
E-commerce Product Listings (if data updates are infrequent, use ISR for periodic revalidation).
SSR ensures fresh data, while SSG boosts performance with pre-rendered content. 🚀





Q. How do you implement data fetching in Next.js for SSR (getServerSideProps) and SSG (getStaticProps)?
A. In Next.js, data fetching is handled based on rendering needs:
SSR (Server-Side Rendering) with getServerSideProps fetches data on every request, ensuring real-time updates but increasing server load.
SSG (Static Site Generation) with getStaticProps pre-fetches data at build time, making pages fast but requiring a rebuild for updates.
ISR (Incremental Static Regeneration) extends SSG by allowing periodic updates without a full rebuild, balancing performance and freshness.
SSR is ideal for dynamic, frequently changing content, while SSG is best for static, high-performance pages. 🚀




Q. How would you handle incremental static regeneration (ISR) in Next.js?
A. Incremental Static Regeneration (ISR) in Next.js allows static pages to be updated without a full site rebuild. It works by serving pre-generated static content while regenerating a fresh version in the background after a specified time (revalidate).
This balances performance and freshness, making it ideal for blogs, product listings, and dynamic content that doesn't need real-time updates. Unlike SSR, ISR doesn’t slow down requests and ensures better scalability by reducing server load. 🚀

Q. What are the trade-offs between client-side rendering (CSR), SSR, and SSG?
A. Client-Side Rendering (CSR) loads a minimal HTML shell and fetches data in the browser, making it fast after the initial load but slower for first-time users and less SEO-friendly. Server-Side Rendering (SSR) generates HTML on every request, ensuring fresh content and good SEO but increasing server load and slowing down response time. Static Site Generation (SSG) pre-renders pages at build time, offering the fastest performance and best SEO, but data can become stale unless updated with Incremental Static Regeneration (ISR). The choice depends on balancing performance, SEO, and data freshness. 🚀






Q. How does Next.js handle routing, and how is it different from React Router?
A. Next.js uses file-based routing, where the folder structure inside the pages/ directory automatically defines routes (e.g., pages/about.js becomes /about). It supports dynamic routes (pages/blog/[id].js → /blog/123), API routes (pages/api/), and built-in SSR, SSG, and ISR for optimized performance.
In contrast, React Router uses client-side routing, requiring manual route definitions (<Route path="/about" element={<About />} />). It lacks built-in server-side rendering and relies on external tools for pre-rendering. Next.js is better for SEO and performance, while React Router offers more flexibility for SPAs. 🚀




Q. How would you implement dynamic routing in Next.js?
A. Dynamic routing in Next.js allows pages to handle variable paths using square brackets ([]) in the pages/ directory. When a user visits a dynamic URL (e.g., /blog/123), Next.js matches it to a file like pages/blog/[id].js.
For Static Site Generation (SSG), getStaticPaths defines possible paths at build time, and getStaticProps fetches data for each page. For Server-Side Rendering (SSR), getServerSideProps fetches data on every request, ensuring fresh content. This approach provides SEO benefits, performance optimization, and flexibility based on data freshness needs. 🚀




Q. What are the best practices for handling authentication and protected routes in a Next.js app?
A. Authentication in Next.js can be handled using JWT, sessions, or third-party providers (e.g., NextAuth.js). Protected routes can be secured at different levels:
Middleware-based protection ensures authentication before rendering a page.
Server-side authentication (getServerSideProps) validates users before sending page content.
Client-side protection can be done using React Context or HOCs to restrict access.
Cookies (HttpOnly) or tokens are commonly used for session management.
The best approach depends on security needs, performance trade-offs, and user experience. 🚀





Q. How would you manage global state in a Next.js application?
Global state management in Next.js depends on the complexity of the app:
React Context API – Best for lightweight, app-wide state like themes or authentication. Avoid for frequently updated data to prevent re-renders.
Zustand – A simple, lightweight alternative to Redux for managing reactive, shared state with minimal boilerplate.
Redux Toolkit – Ideal for complex global state (e.g., user sessions, caching). Works well with Next.js via next-redux-wrapper.
React Query / SWR – Best for server-state management (e.g., fetching, caching, revalidating API data). Recommended over Redux for API-heavy apps.
Choosing the right approach depends on state persistence, update frequency, and performance needs. 🚀





Q. What are the pros and cons of using Context API vs. a state management library like Redux or Zustand? 
A. Context API is a lightweight, built-in React solution ideal for managing simple global state like themes and authentication, but it can cause performance issues due to unnecessary re-renders. In contrast, Redux and Zustand are more efficient for complex, frequently updated state, offering better scalability and performance optimizations. While Redux has more boilerplate, Redux Toolkit simplifies it, and Zustand provides a minimalistic alternative. Context API is best for lightweight state, while Redux/Zustand are better for large-scale, dynamic applications. 🚀





Q. How do you handle server-side state synchronization with client-side state in Next.js?
A. In Next.js, server-side state can be synchronized with client-side state using SSR (getServerSideProps) to fetch data on each request, ensuring fresh content. For better UX, React Query or SWR can prepopulate client-side state with server-fetched data and then revalidate in the background. Global state managers like Context or Zustand help persist and share server-fetched data across components. Additionally, Next.js API routes allow dynamic updates without full-page reloads. This approach ensures fast initial loads while keeping client-side data fresh and consistent. 🚀




Q. How would you design a system to fetch and cache data from an API in a React/Next.js app?
A. To efficiently fetch and cache data in a React/Next.js app, use React Query or SWR for automatic caching, background revalidation, and optimized API calls. For pre-rendered pages, leverage getStaticProps (SSG) with revalidation for fast, cached data or getServerSideProps (SSR) for real-time updates. Implement API response caching using Redis or HTTP cache headers (stale-while-revalidate) to reduce redundant requests. Additionally, store fetched data in Zustand or Context API to minimize unnecessary re-fetching across components. This ensures fast performance, reduced API load, and a seamless user experience. 🚀







Q. What are the best practices for handling API errors and loading states in a React app?
A. In a React app, handling API errors and loading states properly improves UX and reliability. Using React Query or SWR simplifies fetching with built-in error and loading state management. Display spinners or skeleton loaders during loading and meaningful error messages when requests fail. For manual fetching, wrap API calls in try-catch blocks and check response status to handle failures gracefully. Implement automatic retries (e.g., exponential backoff) to recover from transient errors. Logging errors with Sentry or other monitoring tools helps debug issues efficiently. These best practices ensure a smooth and resilient API experience. 🚀





Q. How would you implement real-time updates (e.g., WebSockets) in a Next.js application?
A. In a Next.js app, real-time updates can be handled using WebSockets, Server-Sent Events (SSE), or polling. WebSockets (via Socket.io) enable bidirectional communication, ideal for chat apps or live notifications. SSE provides one-way real-time updates, useful for live feeds or stock prices. If WebSockets/SSE aren’t feasible, polling with React Query or SWR (refetchInterval) can periodically fetch updates. WebSockets offer the best low-latency, scalable solution, while polling is a fallback when persistent connections aren’t viable. Choosing the right approach depends on use case, server load, and real-time requirements. 🚀






How would you implement authentication in a Next.js app (e.g., using JWT, OAuth, or session-based authentication)?
Authentication in a Next.js app can be handled using JWT, OAuth, or session-based authentication based on security and scalability needs. JWT is a stateless approach where tokens are stored in HttpOnly cookies and validated on API requests. OAuth allows authentication via third-party providers like Google or GitHub, often managed using NextAuth.js for easy integration. Session-based authentication stores session data in a database like Redis, ensuring secure, server-validated logins. Middleware can protect routes by restricting access to authenticated users. The choice depends on factors like security, scalability, and ease of implementation. 🚀





What are the security considerations when handling authentication on the client and server sides?
Security in authentication requires careful handling on both the client and server sides. On the client, avoid storing sensitive tokens in localStorage or sessionStorage, as they are vulnerable to XSS attacks; instead, use HttpOnly cookies for secure storage. Always validate user input to prevent injection attacks. On the server, implement rate limiting, IP blocking, and brute-force protection to safeguard login endpoints. Use secure password hashing (bcrypt, Argon2) and enforce strong password policies. Implement CORS policies, CSRF protection, and role-based access control (RBAC) to prevent unauthorized access. Always use HTTPS and regularly audit security practices to mitigate vulnerabilities. 🚀





How would you protect routes and ensure only authorized users can access certain pages? 
To protect routes and ensure only authorized users can access certain pages in a Next.js app, use a combination of server-side validation, middleware, and client-side checks. On the server side, validate authentication using getServerSideProps by checking tokens or sessions before rendering the page. On the client side, use global state (Context API, Zustand) to store user roles and redirect unauthorized users. Middleware (middleware.ts) can block access to protected routes before they load, improving security and performance. Implement role-based access control (RBAC) to restrict certain actions based on user permissions. Combining these strategies ensures a secure and seamless user experience. 🚀





Q. What are the different approaches to styling in React (e.g., CSS Modules, Styled Components, Tailwind CSS)? 
A. Styling in React can be done using various approaches, each with its own advantages. CSS Modules provide scoped styles, preventing class name conflicts, making them great for component-based styling. Styled Components use CSS-in-JS, allowing dynamic styling with props and theme support, ideal for component-level customization. Tailwind CSS offers utility-first styling, reducing the need for writing custom CSS and improving maintainability. Other options include SASS/SCSS for enhanced CSS features, Vanilla CSS for simplicity, and Chakra UI or Material-UI for pre-built component libraries. The choice depends on project complexity, scalability, and developer preference. 🚀




Q. How would you implement a theme system (light/dark mode) in a React/Next.js app?
A. To implement a theme system in a React/Next.js app, use Context API or Zustand to manage the theme state globally. Store the user's preference in localStorage or cookies to persist settings across sessions. Use CSS variables or Tailwind’s dark mode for styling adjustments. The useEffect hook can detect the system's preferred theme and apply it dynamically. For server-side rendering in Next.js, sync the theme using middleware or pass it via getServerSideProps. Libraries like next-themes simplify this process by handling storage and class toggling efficiently. This ensures a smooth, user-friendly theme switching experience. 🚀




Q. What are the pros and cons of using CSS-in-JS vs. traditional CSS?
A. CSS-in-JS and traditional CSS each have their own strengths and trade-offs. CSS-in-JS (e.g., Styled Components) offers scoped styles, dynamic theming, and better maintainability in component-based architectures, but it adds runtime overhead and can impact performance. Traditional CSS (e.g., CSS files, SASS, CSS Modules) provides better performance, caching, and separation of concerns, but it can lead to global style conflicts and less flexibility for dynamic styling. CSS Modules help mitigate global conflicts while keeping performance intact. The choice depends on project complexity, performance needs, and developer preference. 🚀




Q. How would you design a chat app?
A. A chat app system uses a React/Next.js frontend, a Node.js backend with WebSockets for real-time messaging, and a MongoDB/PostgreSQL database for storing chats. Redis caching improves performance, while message queues (Kafka/RabbitMQ) ensure reliable delivery. Authentication (JWT/OAuth) secures user access, and end-to-end encryption protects messages. Load balancing, sharding, and CDN caching help scale the system. A microservices approach can be used for better modularity. This ensures a fast, secure, and scalable real-time chat experience. 🚀




Q. Micro-Frontends vs. Monolithic Architecture
A. Micro-Frontends and Monolithic Architecture differ in scalability, maintainability, and complexity.
Micro-Frontends break the UI into smaller, independently deployable applications, making them ideal for large teams, gradual upgrades, and tech-agnostic solutions. However, they add complexity in communication, performance overhead, and coordination challenges.
Monolithic Architecture keeps everything in a single codebase, offering simpler development, better performance, and easier state management, but it becomes harder to scale, update, or work on independently as the project grows.
The choice depends on team size, scalability needs, and project complexity. 🚀



Q. CDNs & Image Optimization
A. A CDN (Content Delivery Network) improves performance by caching and serving images from edge servers closer to users, reducing latency and load on the origin server. Image optimization involves techniques like lazy loading, compression (WebP, AVIF), responsive images, and caching to improve load times. In Next.js, the next/image component handles automatic optimization, resizing, and lazy loading, reducing bandwidth usage. Using a CDN with optimized images ensures faster load times, reduced server load, and better user experience. 🚀




Q. What are MicroServices?
A. Microservices is an architectural style where an application is divided into small, independent services that communicate via APIs. Each service handles a specific functionality (e.g., authentication, payments, notifications) and can be developed, deployed, and scaled independently. This improves scalability, fault isolation, and tech flexibility but adds complexity in communication, deployment, and monitoring. Common tools include Docker, Kubernetes, API gateways, and message queues (Kafka/RabbitMQ). Microservices are ideal for large, scalable applications requiring high availability and independent deployments. 🚀




Q. Swiggy, Zomato, Netflix System Design
A. Swiggy/Zomato System Design (Food Delivery App)
A scalable, real-time system with separate services for users, restaurants, delivery partners, and payments.
Architecture: Microservices-based (User, Order, Restaurant, Delivery, Payment).
Database: SQL (PostgreSQL) for structured data, NoSQL (MongoDB) for menus & reviews.
Real-time Updates: WebSockets for live order tracking, Redis for caching.
Scalability: Load balancers (NGINX), CDN for images, and sharding for databases.
Routing & Mapping: Google Maps API for route optimization and ETA calculation.
Payments: Secure transactions via Razorpay/Stripe with fraud detection mechanisms.
High Availability: Kubernetes for container orchestration and auto-scaling.
This ensures fast, reliable food ordering, tracking, and delivery at scale. 🚀

Netflix System Design (Video Streaming App)
A highly scalable, low-latency system for seamless video streaming.
Architecture: Microservices-based (User, Content, Streaming, Recommendation, Payments).
Content Storage: AWS S3 or custom CDN for video delivery with regional caching.
Streaming Protocols: Adaptive Bitrate Streaming (HLS, DASH) for smooth playback.
Recommendation Engine: AI-driven personalization using user behavior & metadata.
Database: SQL (User data, payments), NoSQL (Cassandra) for large-scale metadata.
Load Balancing & Caching: Edge caching via CDN (Cloudflare, Akamai) reduces latency.
Scalability: Auto-scaling with Kubernetes, microservices communication via gRPC.
This ensures fast, buffer-free streaming with personalized recommendations. 🚀



Q. Sharding – In-Depth Explanation
A. Sharding is a horizontal database scaling technique that divides large datasets into smaller, manageable parts (shards) and distributes them across multiple servers. Each shard stores a subset of the data, reducing the load on a single database and improving performance, scalability, and availability.
Why is Sharding Needed?
As applications grow, a single database may face performance bottlenecks, slow queries, and high latency. Sharding helps by:
Reducing Query Load – Each query runs on a smaller dataset, making lookups faster.
Handling More Users – Spreads traffic across multiple servers.
Preventing Single Points of Failure – If one shard goes down, others remain unaffected.
Enabling Geo-Distribution – Data can be placed closer to users for faster access.
Types of Sharding
Range-Based Sharding – Data is divided based on a range (e.g., Users with IDs 1-1000 in Shard 1, 1001-2000 in Shard 2). Simple but may lead to unbalanced loads.
Hash-Based Sharding – Uses a hash function to distribute data evenly, avoiding hotspots.
Geographic Sharding – Users are sharded based on their location (e.g., North America, Europe, Asia).
Feature-Based Sharding – Data is divided based on a specific attribute (e.g., customers vs. products).
Challenges of Sharding
Complexity – Managing multiple databases increases maintenance overhead.
Cross-Shard Queries – Queries involving multiple shards are harder to execute efficiently.
Rebalancing – If one shard grows too large, redistributing data is challenging.
Data Consistency – Transactions across shards require additional handling.
