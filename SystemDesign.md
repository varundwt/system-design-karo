How would you structure a large-scale React application to ensure maintainability and scalability?
2. एक folder स्ट्रक्चर बनाना होता है जिससे separation of concerns रहता है, मतलब फाइल्स segregated रहती है। 
3. Atomic Design होना चाहिए मतलब कंपोनेंट्स को जितना हो सके उतना छोटे टुकड़ों मैं तोड़ के रखना। buttons, input बॉक्स अलग, forms, cards एकसाथ वगैरह।  
4. हर component अपनी styles, tests, और logic खुद मैनेज करे अलग फोल्डर मैं.
5. State Management मैं Local स्टेट के लिए useState या useReducer use हो, Global के लिए Context API या Redux use हो और Server स्टेट के लिए React Query , SWR वगैरह.
6. Use React Router for navigation.
7. Use lazy loading and dynamic imports (React.lazy()).
8. Optimize re-renders with useMemo, useCallback, and React.memo.
9. Enable server-side rendering (SSR) or static site generation (SSG) for Next.js.
10. Linting & Formatting: Use ESLint, Prettier, Husky (for pre-commit hooks).
11. Testing: Use Jest, React Testing Library, Cypress for unit/integration/e2e testing.
12. CI/CD: Automate deployments using GitHub Actions, Vercel, or Netlify.
13. Store sensitive data in .env files.
14. Secure API calls with auth tokens and refresh mechanisms.
15. Prevent XSS attacks by sanitizing user input.
* SWR मतलब stale-while-revalidate, इसमें पहले data cache (stale) से return होता है फिर API request send होती है और फिर finally up-to-date data आता है
