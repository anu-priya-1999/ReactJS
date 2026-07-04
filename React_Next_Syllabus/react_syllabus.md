# The Ultimate 2026 React Syllabus: SDE2 to Staff+

> **What changed for 2026?** AI/LLM integration is no longer optional—streaming token UIs are a standard expectation. React Router v7 has merged with Remix. Edge rendering is the default for modern frameworks. Feature-Sliced Design (FSD) has overtaken traditional folder structures. XState v5 is the gold standard for complex state.
> 
> *Look for the 🆕 tag to see exactly what was added to bring your syllabus into 2026.*

---

# PART 1: FOUNDATIONS & PREREQUISITES

## 1.1 JavaScript ES6+ Deep Dive
- **Modern Syntax**: Arrow functions, template literals, destructuring, spread/rest
- **Variables**: `let`, `const`, `var` (scope, TDZ, hoisting)
- **Array Methods**: `map`, `filter`, `reduce`, `find`, `some`, `every`, `sort`, `flatMap`
- **Object Manipulation**: Spread operator, `Object.assign`, computed properties, `Object.freeze`, `Object.seal`
- **Modules**: ES6 `import`/`export` syntax, dynamic imports
- **Asynchronous JavaScript**: Promises, `async/await`, error handling, `Promise.all`, `Promise.race`, `Promise.allSettled`, `Promise.any`
- **Classes & OOP**: Inheritance, `super`, static methods, private fields
- **Optional Chaining & Nullish Coalescing**: `?.`, `??`
- **WeakMap / WeakSet** (for memory management in caches)

## 1.2 Development Environment Setup
- Node.js v20+ and npm/yarn/pnpm
- Create React App (deprecated) vs Vite vs Webpack vs Rspack vs 🆕 **Turbopack (Production-ready) / Farm**
- Browser Developer Tools
- React DevTools extension (Profiler, Components)
- Redux DevTools
- VS Code setup (ESLint, Prettier, Tailwind CSS, React snippets)

---

# PART 2: REACT CORE CONCEPTS (SDE2)

## 2.1 Introduction to React
- What is React? Virtual DOM concept
- Component-based architecture
- JSX syntax and rules, reconciliation
- Expressions in JSX, conditional rendering
- React elements vs components
- **Strict Mode** – double invocation, detecting side effects

## 2.2 Components & Props
- Component types (Functional vs Class)
- Rendering flow & lifecycle methods (class) vs hooks (functional)
- Props vs State
- Controlled vs Uncontrolled components
- Keys in lists and reconciliation pitfalls
- Error Boundaries
- PropTypes and TypeScript basics
- Children prop and component composition
- **Portals** (`ReactDOM.createPortal`) – rendering outside parent DOM hierarchy

## 2.3 State Management Fundamentals
- `useState` Hook: initialization, updates, functional updates, lazy initialization
- State immutability rules (never mutate state directly)
- Lifting state up
- State management patterns (component state, app state)

## 2.4 Event Handling
- Synthetic events and pooling (React 17+ no pooling)
- Event handlers (`onClick`, `onChange`, `onSubmit`)
- Passing arguments to event handlers
- Form handling basics
- **React 19**: `ref` as a prop (no more `forwardRef` needed)

---

# PART 3: ESSENTIAL REACT HOOKS (SDE2 → SDE3)

## 3.1 Basic Hooks
- `useState` – with functional updates and batching
- `useEffect` – lifecycle simulation, cleanup, dependencies, stale closure solutions
- `useContext` – consuming context (React 19: `use` API alternative)
- `useRef` – DOM access, mutable values, previous value tracking

## 3.2 Additional Hooks (React 16.8 – 18)
- `useReducer` – complex state logic (when state transitions are interrelated)
- `useCallback` – memoizing functions, dependency array best practices
- `useMemo` – memoizing expensive computations
- `useImperativeHandle` – exposing child methods to parent
- `useLayoutEffect` – synchronous DOM mutations (before paint)
- `useDebugValue` – custom hook labeling in DevTools
- `useId` – stable IDs for accessibility (hydration-safe)
- `useTransition` – marking non-urgent updates, `isPending`
- `useDeferredValue` – deferring non-critical UI updates
- **`useSyncExternalStore`** (React 18) – subscribing to external stores (Redux, Zustand, browser APIs) with concurrency safety
- **`useInsertionEffect`** (React 18) – for CSS-in-JS dynamic style injection (avoids layout thrashing)

## 3.3 React 19+ Hooks
- **`useOptimistic`** – optimistic UI updates with automatic rollback
- **`useFormStatus`** – access form submission status without prop drilling
- **`useActionState`** – unified form state management with actions
- **`use` API** – read promises and context with Suspense (replaces `useContext` in some cases, works in conditionals/loops)

## 3.4 React Compiler (formerly "Forget")
- Automatic memoization – how it changes `useMemo`/`useCallback` best practices
- Compiler directives – `"use memo"`, `"use no memo"`
- Adoption strategy in existing codebases
- 🆕 **Understanding the React Signals Proposal** (How the Compiler maps to future React primitives)

## 3.5 Custom Hooks
- Creating custom hooks
- Hook composition and reuse
- Common patterns: `useDebounce`, `useThrottle`, `useLocalStorage`, `useFetch`, `usePrevious`, `usePolling`, `useWebSocket`, `useClickOutside`, `useIntersectionObserver`
- Rules of Hooks (call only at top level, only from React functions)

---

# PART 4: ADVANCED REACT CONCEPTS (SDE2 → SDE3)

## 4.1 Performance Optimization
- `React.memo` – component memoization, custom comparison function
- `useMemo` / `useCallback` optimization patterns (when to use, when to avoid)
- Avoiding unnecessary re-renders: lifting state down, children as props, component composition
- Virtualized lists (`react-window`, `@tanstack/react-virtual`) for large datasets (10k+ rows)
- Code splitting: `React.lazy`, `Suspense`, dynamic imports
- Bundle splitting strategies – route-based, component-based, vendor splitting
- Tree-shaking and side effects configuration (`sideEffects: false`)
- Profiling with React DevTools (flamegraphs, ranked charts, interactions)
- **`Why Did You Render?`** library – tracking re-renders
- **Web Vitals** (LCP, CLS, INP, FID) optimization techniques

## 4.2 Context API Advanced
- Creating and providing context
- Consuming with `useContext` (or `use` API in React 19)
- Performance pitfalls – one context re-renders all consumers
- Solutions: splitting contexts, memoizing value, selector-based context (using `useSyncExternalStore`)
- React 19: `Context` as a provider (no need for `Context.Provider`)

## 4.3 Refs and DOM Manipulation
- `useRef` for DOM access
- Forwarding refs – React 19: `ref` is a normal prop, no `forwardRef` needed
- Callback refs (when you need to know when a DOM node is attached/detached)
- 🆕 **Ref Cleanup Functions (React 19)** – returning a cleanup function from ref callbacks for `ResizeObserver`/`IntersectionObserver`.
- Use cases: focus management, media playback, third-party library integration

## 4.4 Error Boundaries
- Creating error boundaries with `getDerivedStateFromError` and `componentDidCatch`
- Limitations: do not catch errors in event handlers, async code, or the error boundary itself
- Error recovery patterns (fallback UI, resetting state, logging to Sentry)
- **Hydration errors** – common causes and solutions

## 4.5 Suspense & Concurrent Features
- `Suspense` for code-splitting and data fetching
- Data fetching with Suspense – using `use` API or Relay/SWR
- Concurrent rendering: how React interrupts renders for high-priority updates
- `startTransition` and `useTransition` for non-urgent updates

---

# PART 5: FORMS & VALIDATION (SDE2)

## 5.1 Form Management
- Controlled forms (state-driven) – pros/cons
- Uncontrolled forms (refs) – when to use (file inputs, third-party widgets)
- Form libraries: **React Hook Form** (modern, performant), Formik (legacy)
- Validation libraries: **Zod** (recommended), Yup, Joi
- Custom validators & async validation (checking username availability)
- Error messages and accessibility (ARIA `aria-invalid`, `aria-describedby`)
- Dynamic form builder from JSON schema
- 🆕 **Complex State Machines in Forms (XState v5)** – Managing multi-step, async, or highly branching form flows.

## 5.2 React 19 Form Actions
- `useActionState` for pending states, errors, and return values
- `useFormStatus` for nested component submission status
- Progressive enhancement with Server Actions (Next.js)

---

# PART 6: ROUTING & NAVIGATION (SDE2)

## 6.1 🆕 React Router v7 (The Remix Merge)
- **Framework Mode vs Library Mode**
- Routes, nested routes, dynamic params (`:id`)
- Navigation: `Link`, `NavLink`, `useNavigate`
- URL parameters (`useParams`) and query strings (`useSearchParams`)
- Protected routes and authentication flows
- Route-based code splitting (lazy loading with `Suspense`)
- **Loaders and Actions** – data fetching before render, handling mutations (now standard in RRv7)
- `useLoaderData`, `useActionData`, `useFetcher`

## 6.2 Advanced Routing
- Route guards / navigation blockers (`useBlocker`)
- Breadcrumb implementation (dynamic from route matches)
- Scroll restoration (`ScrollRestoration` component)
- Animated transitions (Framer Motion with routes)
- 🆕 **Browser `Navigation API` integration** (Replacing traditional History API listening for modern SPA routing).

---

# PART 7: STATE MANAGEMENT SOLUTIONS (SDE2 → SDE3)

## 7.1 Client State Management
- **Local state** (useState, useReducer)
- **Context API** (scoped global state) – for theme, auth, language
- **Redux Toolkit** (modern Redux)
  - Store configuration, slices, reducers
  - `createAsyncThunk` for async actions
  - RTK Query for data fetching with caching
  - Selectors with `createSelector` (reselect)
- **Zustand** (lightweight alternative) – with persistence, middleware, devtools
- **Recoil** / **Jotai** (atomic state) – for fine-grained subscriptions
- 🆕 **XState v5** – Actor-model based state machines. *Critical for 2026 SDE3 roles to manage complex, guaranteed state transitions (e.g., checkout flows, multi-step wizards).*

## 7.2 Server State Management
- **TanStack Query (React Query) v5**
  - Queries and mutations
  - Cache management, `staleTime`, `gcTime`
  - Background updates, `refetchOnWindowFocus`
  - Optimistic updates (update cache before mutation)
  - Infinite queries and pagination
  - Prefetching and placeholder data
- **SWR** (Vercel) – alternative with different trade-offs

## 7.3 Data Fetching Patterns & UIs
- Fetch API, Axios, graphql-request
- Error handling strategies (try/catch, error boundaries)
- `AbortController` for canceling in-flight requests
- Debounce & throttle in search inputs
- Infinite scroll + pagination (scroll-based or button-based)
- WebSockets / SSE for real-time updates (chat, live data)
- Polling utilities (auto-refresh dashboard every 30 seconds)
- Request deduplication and caching
- 🆕 **TanStack Table v8** – The industry standard for building complex, headless data grids (sorting, filtering, pagination, row selection, virtualization) in React.
- 🆕 **AI/LLM Streaming UIs** – Managing streamed token states, rendering markdown incrementally, aborting AI generation requests.

## 7.4 Authentication & Authorization
- Authentication patterns (JWT, refresh tokens rotation)
- Social logins (OAuth – Google, GitHub)
- Protected routes and role-based access control (RBAC)
- Feature flags (LaunchDarkly, custom hooks)
- Session handling – cookies vs localStorage vs httpOnly secure cookies (security trade-offs)
- CSRF, XSS protections in React (CSP headers, sanitization)
- **`useAuth` hook** with JWT refresh, token storage, and automatic retry

---

# PART 8: STYLING & UI (SDE2)

## 8.1 Styling Approaches
- CSS Modules (scoped, local classes)
- Styled Components / Emotion (CSS-in-JS) – runtime performance and `useInsertionEffect`
- Tailwind CSS (utility-first) – with twin.macro or PostCSS
- 🆕 **Zero-Runtime CSS-in-JS (vanilla-extract, Linaria, Panda CSS)** – The 2026 standard for performance-critical apps. Extract styles at build time.
- SASS/SCSS integration (variables, mixins)
- Responsive design in React (CSS media queries, useMediaQuery hook, Container Queries)
- Theme switching (dark mode, system preference via `prefers-color-scheme`)

## 8.2 UI Libraries & Design Systems
- Material-UI (MUI), Ant Design, Chakra UI, Radix UI, Shadcn/ui
- Headless UI components (Radix UI, Headless UI by Tailwind) – unstyled accessible components
- Building custom component libraries (Storybook, changesets)
- **Design tokens** – W3C format, Style Dictionary

## 8.3 Animation
- CSS Transitions/Animations with React
- Framer Motion (declarative, gesture support)
- React Spring (physics-based)
- Layout animations (FLIP technique – First, Last, Invert, Play)
- 🆕 **View Transitions API** – Native browser API for page/component transitions (now supported in React frameworks).
- `will-change` and GPU acceleration tips
- Skeleton loaders (react-loading-skeleton, custom)

---

# PART 9: TESTING & DEBUGGING (SDE2 → SDE3)

## 9.1 Testing Fundamentals
- Vitest (replacing Jest for Vite/Turbopack ecosystems) / Jest configuration
- React Testing Library principles ("testing like a user")
- Snapshot testing (use sparingly, when UI is stable)

## 9.2 Testing Strategies
- Unit testing React components (isolated)
- Integration testing user flows (multiple components together)
- End-to-end testing (Playwright is the 2026 standard; Cypress is legacy)
- Testing custom hooks (`renderHook` from RTL)
- Testing async components (waitFor, findBy)
- Testing error boundaries
- **Mock Service Worker (MSW 2.0)** – intercept network requests at the service worker level
- 🆕 **Visual Regression Testing** – Chromatic, Percy, or Vercel Preview. *Crucial for Design Systems and senior roles to prevent UI drift.*

## 9.3 Debugging & Profiling
- React DevTools profiler (flamegraphs, ranked charts, interactions timeline)
- `useDebugValue` for custom hook labeling
- Component stacks in errors (React 18+ improvements)
- Source maps in production (trade-offs: debuggability vs size)
- **React Scan** – new tool for detecting render performance issues
- Core Web Vitals (LCP, CLS, INP, FID) – measuring and optimizing
- `reportWebVitals` and sending data to analytics
- 🆕 **OpenTelemetry for React** – Distributed tracing for frontend requests to trace errors across microservices.

---

# PART 10: ADVANCED PATTERNS & ARCHITECTURE (SDE3)

## 10.1 Design Patterns
- Compound components (Headless UI style) – Tabs, Menu, Select
- Render props pattern (data fetching, mouse tracking)
- Higher-order components (HOCs) – legacy, used for cross-cutting concerns
- Custom hook patterns (encapsulating stateful logic)
- Provider pattern (Context + reducer)
- Controlled vs uncontrolled component patterns

## 10.2 Application Architecture
- 🆕 **Feature-Sliced Design (FSD)** – The modern enterprise standard for organizing React apps (layers: app, processes, pages, widgets, features, entities, shared).
- Configuration management (environment variables, build-time vs runtime)
- Error handling strategies (global boundary + local fallbacks)
- Logging and monitoring (Sentry, OpenTelemetry, Datadog)
- Feature flags and A/B testing integration with React

## 10.3 Micro-frontends
- Concept and use cases (independent deployments, team autonomy)
- Module Federation (Webpack 5 / Rspack) – remote entry points
- Shared dependency versioning (singleton, eager loading)
- Communication patterns – custom events, global store (Redux/Zustand across apps)
- 🆕 **Native Federation** (Using Vite/Rspack instead of Webpack for MFEs).
- Single-SPA framework for orchestration

## 10.4 Monorepo & Code Sharing (SDE3)
- Turborepo / Nx setup with React
- Sharing components, hooks, types across multiple apps (UI library as a package)
- Versioning and publishing component libraries (SemVer, changesets)
- Bit / Storybook for component discovery and documentation

---

# PART 11: SERVER-SIDE RENDERING & FRAMEWORKS (SDE3)

## 11.1 Next.js (App Router v14/v15) – Complete
- File-based routing and folder conventions (app directory)
- **Server Components (RSC)** – when to use, benefits (no client JS)
- **Client Components** (`"use client"`) – interactive parts
- Data fetching: `fetch` with caching (extended `fetch`), `async` components
- Static Site Generation (SSG) – `generateStaticParams`
- Server-Side Rendering (SSR) – dynamic rendering per request
- Incremental Static Regeneration (ISR) – `revalidate` and `next.revalidate`
- Streaming with Suspense and `loading.js`, `error.js`
- Server Actions (`"use server"`) for mutations (replaces API routes for forms)
- Middleware (auth, redirects, rewrites, geolocation)
- Image optimization (`next/image`), Font optimization (`next/font`)
- API Routes (Route Handlers) – alternative to Server Actions
- Metadata API (SEO) – static and dynamic
- 🆕 **Partial Prerendering (PPR)** – Combining static shell with dynamic streaming holes.

## 11.2 React Server Components (RSC) Deep Dive
- How RSC differs from SSR (no hydration, zero client bundle)
- Mixing server and client components – pattern "move down the client boundary"
- Direct database calls in RSC (no API layer needed)
- Streaming with `<Suspense>` and progressive rendering
- RSC payload format (JSON-like, with references)

## 11.3 Alternative Frameworks & Edge SSR
- Remix (now merged into React Router v7)
- Gatsby (static site generation, GraphQL data layer)
- 🆕 **Edge Rendering** – Cloudflare Workers, Vercel Edge Functions, Deno Deploy. Running React/SSR at the edge for ultra-low TTFB.
- React Native (mobile) – basics for cross-platform knowledge

---

# PART 12: REAL-WORLD PROJECT SKILLS

## 12.1 Project Setup & Tooling
- ESLint and Prettier configuration (flat config format in 2026)
- Git hooks with Husky, lint-staged
- Absolute imports configuration (using `jsconfig.json` or `tsconfig.json` paths)
- Environment-specific configs (`.env.development`, `.env.production`)
- Custom Webpack loaders/plugins (e.g., `webpack-bundle-analyzer`)
- ESBuild / SWC for faster transpilation

## 12.2 CI/CD for React
- GitHub Actions / GitLab CI pipelines (build, test, deploy)
- Environment-specific builds (dev/staging/prod with different API URLs)
- Deploy to Netlify, Vercel, AWS S3 + CloudFront, or serverless
- Docker containerization for SSR apps

## 12.3 Security in React Apps (Critical for SDE3)
- XSS prevention – never use `dangerouslySetInnerHTML` with unsanitized data; use DOMPurify if needed
- CSRF protection – SameSite cookies, anti-CSRF tokens
- Content Security Policy (CSP) with React – restricting script sources
- Sanitizing user-generated HTML (DOMPurify, sanitize-html)
- JWT storage – localStorage (vulnerable to XSS) vs httpOnly cookie (vulnerable to CSRF) – trade-offs and best practices (use `SameSite=Strict` + CSRF tokens)
- Preventing prototype pollution (freeze objects, use `Object.create(null)`)

## 12.4 Offline & PWA
- Service workers with Workbox (caching strategies: stale-while-revalidate, network-first)
- IndexedDB wrapper – localForage, Dexie for structured data
- Background sync (for offline mutations)
- Update-on-connect conflict resolution (last-write-wins, version vectors)
- PWA manifest and installability (add to home screen)
- 🆕 **`BroadcastChannel` API** – Syncing state across multiple browser tabs in real-time without a server.

---

# PART 13: INTERNATIONALIZATION & ACCESSIBILITY

## 13.1 Internationalization (i18n)
- `react-intl` / `formatjs` – message extraction, IDs
- Pluralization, date/number formatting (Intl API)
- RTL (right-to-left) layout support (CSS logical properties, dir attribute)
- Dynamic language loading (code splitting per locale)
- Translatable content management

## 13.2 Accessibility (a11y)
- WCAG 2.1 / 2.2 guidelines (A, AA, AAA) – focus on Level AA
- ARIA attributes and roles when semantic HTML is insufficient
- Keyboard navigation – focus management, `tabindex`, skip links
- Screen reader testing (VoiceOver, NVDA, JAWS)
- Automated accessibility testing (axe-core, jest-axe, @testing-library/jest-dom matchers)
- Focus trapping in modals and popovers (useFocusTrap hook)

---

# PART 14: ADVANCED TYPESCRIPT WITH REACT (SDE3)

## 14.1 Core TypeScript for React
- `React.FC` vs explicit prop typing – trade-offs
- `ComponentPropsWithoutRef`, `ComponentPropsWithRef`, `ComponentProps`
- `React.ElementRef` – getting element type from ref
- `React.ElementType` – polymorphic components

## 14.2 Generic Components
```tsx
function Select<T extends string = string>({ options, value, onChange }: SelectProps<T>) {}
```

## 14.3 Polymorphic Components
- `as` prop pattern – type-safe with `ElementType` and `ComponentPropsWithoutRef`
- Using `PolymorphicComponentProps` generic type

## 14.4 Advanced Utility Types
- `Omit`, `Pick`, `Partial`, `Required`, `Record`
- `Exclude`, `Extract`, `NonNullable`, `ReturnType`, `Parameters`
- Template literal types (e.g., `${string}Id`)
- `infer` keyword for advanced conditional types
- `satisfies` operator – type checking without widening

## 14.5 Type-Safe Context & Hooks
- Discriminated unions for complex state (loading, success, error states)
- Context with `createContext` and typed `useContext`
- Type-safe event handlers – `React.ChangeEvent<HTMLInputElement>`

---

# PART 15: REAL-TIME, COLLABORATION & AI (SDE3)

## 15.1 WebSockets & Server-Sent Events
- Reconnecting WebSocket with exponential backoff
- SSE (EventSource) for one-way streaming
- `useWebSocket` custom hook with reconnect and heartbeat

## 15.2 Collaborative Editing
- **CRDT** vs **OT** – trade-offs, complexity, latency, offline support
- **Yjs** library – practical implementation (shared types, awareness)
- WebRTC for peer-to-peer data sync (no central server)
- Presence and cursor tracking
- Operational Transformation basics (used in Google Docs)

## 15.3 Live Dashboard & Data Streaming
- Real-time charts (WebSocket + Chart.js / Recharts / Viz)
- Throttling updates to 60fps (skip frames)
- Virtualized real-time tables (TanStack Virtual + streaming data)

## 15.4 🆕 AI/LLM UI Integration (2026 Standard)
- **Streaming Text UIs**: Consuming Server-Sent Events (SSE) or ReadableStreams from LLM APIs (OpenAI, Anthropic) chunk-by-chunk.
- **Tool Calling UIs**: Rendering dynamic UI components based on structured JSON responses from AI function calling.
- **State Management for AI**: Handling `pending`, `streaming`, `success`, and `error` states for generative UI.
- **Abort Controllers for AI**: Allowing users to stop a long-running LLM generation mid-stream.

---

# PART 16: GRAPHQL IN REACT (SDE3)

## 16.1 Apollo Client Advanced
- Normalized caching with `InMemoryCache` and `typePolicies`
- Pagination – offset-based, cursor-based with `fetchMore` and `@connection`
- Subscriptions (WebSocket) with Apollo Client (`split` link)
- Code generation (GraphQL Code Generator) for type safety
- Optimistic mutations (update cache before response)
- Reactive variables for local state

## 16.2 Alternatives
- Relay (Meta-style, high performance, complex learning curve)
- urql (lightweight, modular)
- 🆕 **TanStack GraphQL** – The modern, typesafe, lightweight GraphQL client from the TanStack ecosystem.

---

# PART 17: ADVANCED BUILD & DEPLOYMENT

## 17.1 Bundle Optimization
- Tree shaking – ensure modules are side-effect free (`sideEffects: false` in `package.json`)
- Dynamic imports and chunk splitting (`webpackChunkName` magic comment)
- Bundle analysis – `webpack-bundle-analyzer`, `vite-bundle-visualizer`
- Module Federation advanced – remote versioning, shared scope
- Environment variables in build time (`process.env` in CRA, `import.meta.env` in Vite)

## 17.2 Performance Monitoring
- Core Web Vitals (LCP, CLS, INP, FID)
- Real User Monitoring (RUM) – Sentry, DataDog, New Relic
- Lighthouse CI (enforce performance budgets)
- Measuring TTI (Time to Interactive) and TBT (Total Blocking Time)

---

# PART 18: SYSTEM DESIGN WITH REACT (SDE3+)

## 18.1 High-Level Design Process (RADIO Method)
- **R**equirements – functional and non-functional (real-time, offline, scale)
- **A**PI design – REST or GraphQL, WebSocket events
- **D**ata model – client-side vs server-side state, cache shapes
- **I**nfrastructure – WebSockets, Redis pub/sub, CDN, load balancers
- **O**perations – scaling, retry logic, reconnection, offline sync

## 18.2 Common System Design Questions
| Problem                                    | Expected Components                                                                             |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| Collaborative text editor (Google Docs)    | CRDT/OT, WebSockets, cursor/presence, operation transforms                                      |
| Real-time dashboard (live charts)          | WebSocket, throttling, virtualization, subscription management                                  |
| Design system / component library          | Tokenization, theming, Storybook, versioning, visual regression testing (Chromatic)             |
| Micro-frontend architecture for e-commerce | Module Federation (Native/Vite), shared deps, cross-app communication (BroadcastChannel)        |
| Offline-first PWA                          | Service workers, IndexedDB, sync queue, conflict resolution                                     |
| Video conferencing UI (Zoom clone)         | WebRTC, media streams, signaling server, SFU/MCU                                                |
| 🆕 AI Chat Interface (ChatGPT clone)        | Streaming SSE, token state management, markdown rendering, abort controllers, tool UI rendering |

## 18.3 Trade-off Discussions
- OT vs CRDT (complexity, convergence guarantees, network overhead)
- Client-side state vs server-side state (latency vs consistency)
- Optimistic updates vs error handling (UX vs data integrity)
- CSR vs SSR vs SSG vs Edge SSR (SEO, interactivity, TTFB, server load)
- Monorepo vs multirepo (code sharing vs team autonomy)
- 🆕 Runtime CSS-in-JS vs Zero-Runtime CSS-in-JS (Developer Experience vs Bundle Size)

---

# PART 19: REACT DEVTOOLS & PROFILING DEEP DIVE

## 19.1 Profiler Tab
- Recording interactions and renders
- Flamegraph – understanding render duration and commit phases
- Ranked chart – which components took the longest
- Interactions timeline – user-triggered updates

## 19.2 Components Tab
- Props and state inspection
- Hooks values
- Highlight updates when components render
- Debugging context providers and consumers

## 19.3 Performance Best Practices Checklist
- [ ] Use React DevTools profiler to identify slow components
- [ ] Virtualize long lists
- [ ] Implement `React.memo` for pure components that receive the same props often
- [ ] Avoid inline objects/functions in JSX that break memoization
- [ ] Use `useCallback` for event handlers passed to memoized children
- [ ] Code-split routes and heavy components
- [ ] Optimize images and use lazy loading
- [ ] Measure Core Web Vitals with `next/script` (or similar)

---

# PART 20: PROJECT IDEAS BY LEVEL

## Beginner Projects
- Todo App with local storage (CRUD, filtering)
- Weather App with OpenWeatherMap API
- Calculator with history and keyboard support
- Markdown Blog with `react-markdown`

## Intermediate Projects
- E-commerce product listing with cart (Context API, pagination, filters)
- Social Media Dashboard (real-time updates via WebSocket)
- Project Management Tool (Kanban with drag-and-drop using @dnd-kit)
- Chat Application (WebSocket, user presence, typing indicators)

## Advanced Projects (SDE2 Showcase)
- Real-time Collaboration Tool (Google Docs clone – Yjs, WebSocket)
- Analytics Dashboard (charts, live data, export to CSV/PDF)
- Design System with Storybook + Chromatic visual testing
- Micro-frontend Demo with Module Federation (host + remote app)

## Expert Projects (SDE3 Showcase)
- Full-stack SaaS with Next.js (RSC, Server Actions, authentication, payment)
- Offline-first PWA with IndexedDB + sync engine (Task management app)
- Video Conferencing UI (WebRTC, screen share, recording)
- 🆕 AI-Native Workspace (Chat interface with streaming responses, tool-calling UI, RAG document querying).
- Large-scale Data Grid (TanStack Table + Virtual, inline editing, sorting, filtering, 100k rows)

---

# PART 21: INTERVIEW PREPARATION CHECKLIST

## SDE2 – Must Master
- [ ] React fundamentals (JSX, components, props, state)
- [ ] Hooks: `useState`, `useEffect`, `useRef`, `useContext`
- [ ] Controlled vs uncontrolled components
- [ ] Keys and reconciliation
- [ ] React Router v7 basics (Routes, Link, useNavigate, useParams)
- [ ] Forms (React Hook Form + Zod)
- [ ] Context API for global state (theme, auth)
- [ ] Basic performance (`React.memo`, `useCallback`, `useMemo`)
- [ ] Testing (Vitest/Jest, RTL, userEvent, MSW basics)
- [ ] Basic TypeScript (interfaces, typing props)
- [ ] Accessibility basics (semantic HTML, ARIA labels, keyboard nav)

## SDE3 – Additional Mastery
- [ ] All hooks including `useReducer`, `useLayoutEffect`, `useTransition`, `useDeferredValue`, `useSyncExternalStore`, `useInsertionEffect`, React 19 hooks
- [ ] Advanced performance (virtualization, concurrency, profiling with DevTools)
- [ ] Redux Toolkit / Zustand / React Query (TanStack v5) / XState v5
- [ ] Next.js App Router (RSC, Server Actions, ISR, Partial Prerendering, streaming)
- [ ] Micro-frontends and Module Federation
- [ ] Design patterns (compound, render props, HOCs, custom hooks)
- [ ] Advanced TypeScript (generics, utility types, polymorphic components)
- [ ] Security (XSS, CSRF, CSP, JWT storage trade-offs)
- [ ] System design with React (collaborative editor, live dashboard, AI chat UI)
- [ ] PWA and offline support (Workbox, IndexedDB)
- [ ] Monorepo and code sharing (Turborepo, Feature-Sliced Design)
- [ ] Error tracking and performance monitoring (Sentry, OpenTelemetry)

## Staff+ – Expert Level
- [ ] React Compiler internals (Forget) & React Signals proposal
- [ ] Custom renderers (react-three-fiber, react-pdf)
- [ ] React Native architecture (Fabric, TurboModules)
- [ ] Building an open-source React library
- [ ] Contributing to React core (understanding codebase structure)

---

# QUICK REFERENCE: REACT 19+ NEW FEATURES

| Feature               | Purpose                                                     | Interview Expectation |
| --------------------- | ----------------------------------------------------------- | --------------------- |
| `useOptimistic`       | Optimistic UI updates with auto rollback                    | SDE3                  |
| `useFormStatus`       | Access form submission status in nested components          | SDE2                  |
| `useActionState`      | Unified form state + actions (loading, error, data)         | SDE3                  |
| `use` API             | Read promises/context with Suspense (works in conditionals) | SDE3                  |
| React Compiler        | Automatic memoization (no more useMemo/useCallback)         | SDE3/Staff            |
| Server Actions        | Mutations in RSC (`"use server"`)                           | SDE3                  |
| `ref` as prop         | No more `forwardRef`                                        | SDE2                  |
| `Context` as provider | `<Context>` instead of `<Context.Provider>`                 | SDE2                  |
| Asset loading         | `preload`, `prefetch`, `preconnect` built-in                | SDE2                  |
| 🆕 Ref Cleanup         | Return cleanup fn from ref callbacks                        | SDE3                  |

---

## What Makes This The "2026" Syllabus? (Summary of Upgrades)

1.  **AI Integration:** Added LLM streaming UIs and tool-calling state management (Part 15.4).
2.  **Modern Routing:** Upgraded React Router to v7 (Remix merge) and added the browser Navigation API (Part 6).
3.  **State Machines:** Elevated XState v5 to core state management (Part 7.1).
4.  **Modern Architecture:** Replaced basic feature folders with Feature-Sliced Design (Part 10.2).
5.  **Performance/Build:** Added Zero-Runtime CSS-in-JS (Panda/Linaria), Turbopack/Farm, and Native Federation (Parts 8, 10.3, 12.1).
6.  **Data Grids:** Made TanStack Table a first-class data fetching pattern (Part 7.3).
7.  **Edge Computing:** Added Edge Rendering and Partial Prerendering (PPR) to the SSR section (Part 11).
8.  **Visual Testing:** Upgraded testing to include Visual Regression as a mandatory SDE3 skill (Part 9.2).
9.  **Cross-Tab State:** Added `BroadcastChannel` API for offline/PWA sync (Part 12.4).
10. **React Internals:** Added the React Signals proposal context to the Compiler section (Part 3.4).
