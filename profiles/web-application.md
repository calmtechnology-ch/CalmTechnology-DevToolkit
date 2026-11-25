# Technical Profile: Modern Web Applications

## 1. Architectural Philosophy
Web applications built with or supported by the toolkit must exhibit resilience, responsive performance, full accessibility, and strict security posture across all modern desktop and mobile browsers.

---

## 2. Frontend Architecture & State Management
- **Modular Component Isolation**: Encapsulate UI state within independent, self-contained components.
- **Unidirectional Data Flow**: State mutations must flow strictly in one direction (e.g., Action -> Dispatcher/Reducer -> Store -> View).
- **Error Boundaries**: Every high-level route and major component must be wrapped in an Error Boundary to prevent full application white-screens on unhandled exceptions.
- **Network Resilience**:
  - Implement request retry mechanisms with exponential backoff for transient network errors.
  - Implement offline caching strategies (e.g., Service Workers / IndexedDB) for critical user workflows.

---

## 3. Web Accessibility (a11y)
- **WCAG 2.1 AA Compliance**:
  - Ensure minimum color contrast ratio of 4.5:1 for normal text and 3:1 for large text.
  - Full keyboard navigability (all interactive elements must have visible `:focus-visible` outlines and work with Tab / Enter / Space / Escape).
  - Semantic HTML (`<button>`, `<main>`, `<nav>`, `<article>`) rather than generic `<div>` click listeners.
  - Explicit ARIA attributes (`aria-expanded`, `aria-live`, `aria-label`) where visual context alone is insufficient.

---

## 4. Web Security Posture
- **Content Security Policy (CSP)**:
  - Enforce strict CSP headers preventing `unsafe-inline` script execution.
  - Restrict script, style, and connect sources to explicitly trusted domains.
- **Cross-Site Scripting (XSS) Prevention**:
  - Never render unescaped user-supplied content via `innerHTML` or `dangerouslySetInnerHTML`.
  - Sanitize markdown or rich text using established sanitizers (e.g., DOMPurify).
- **Cross-Origin Resource Sharing (CORS)**:
  - Configure precise API CORS origins; never use wildcard `*` with authenticated credentials (`Access-Control-Allow-Credentials: true`).

---

## 5. Performance Budgets & Asset Optimization
- Target Core Web Vitals:
  - Largest Contentful Paint (LCP) < 2.5s.
  - First Input Delay (FID) / Interaction to Next Paint (INP) < 200 ms.
  - Cumulative Layout Shift (CLS) < 0.1.
- Code-splitting by route to minimize initial JavaScript bundle size (< 150 KB gzipped initial load).
