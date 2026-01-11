# 09: Pattern — Web App

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                          PATTERN: WEB APP                                    ║
║                                                                              ║
║   Use this pattern when: Building interactive applications                   ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │                        FRONTEND                             │    │    ║
║  │   │                    (What user sees)                         │    │    ║
║  │   │                                                             │    │    ║
║  │   │    ┌─────────┐    ┌─────────┐    ┌─────────┐               │    │    ║
║  │   │    │  Page   │    │  Form   │    │ Display │               │    │    ║
║  │   │    └─────────┘    └─────────┘    └─────────┘               │    │    ║
║  │   │                                                             │    │    ║
║  │   └───────────────────────────┬─────────────────────────────────┘    │    ║
║  │                               │                                      │    ║
║  │                               │  Request / Response                  │    ║
║  │                               ▼                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │                        BACKEND                              │    │    ║
║  │   │                    (Logic + Data)                           │    │    ║
║  │   │                                                             │    │    ║
║  │   │    ┌─────────┐    ┌─────────┐    ┌─────────┐               │    │    ║
║  │   │    │  API    │───►│  Logic  │───►│  Data   │               │    │    ║
║  │   │    │ Routes  │    │         │    │ Storage │               │    │    ║
║  │   │    └─────────┘    └─────────┘    └─────────┘               │    │    ║
║  │   │                                                             │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE (bottom up):                                                ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. DATA                                                           │    ║
║   │      "Create a function to store and retrieve items from a list"    │    ║
║   │                                                                     │    ║
║   │   2. LOGIC                                                          │    ║
║   │      "Add functions: add_item, get_items, delete_item"              │    ║
║   │                                                                     │    ║
║   │   3. API                                                            │    ║
║   │      "Create Flask routes: GET /items, POST /items, DELETE /items"  │    ║
║   │                                                                     │    ║
║   │   4. FRONTEND                                                       │    ║
║   │      "Create HTML page with form to add items and list to show them"│    ║
║   │                                                                     │    ║
║   │   5. CONNECT                                                        │    ║
║   │      "Make form submit to API, refresh list on response"            │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   SIMPLE VERSION (single file):                                              ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │       ┌─────────────────────────────────────────────┐               │    ║
║   │       │              index.html                     │               │    ║
║   │       │                                             │               │    ║
║   │       │   HTML (structure)                          │               │    ║
║   │       │   + CSS (style)                             │               │    ║
║   │       │   + JavaScript (behavior)                   │               │    ║
║   │       │                                             │               │    ║
║   │       └─────────────────────────────────────────────┘               │    ║
║   │                                                                     │    ║
║   │   "Create single HTML file with form, styled nicely, that stores    │    ║
║   │    data in browser localStorage"                                    │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## What This Shows

Web apps have frontend (what user sees) and backend (logic + data). Build bottom-up: data → logic → API → frontend → connect. For simple tools, a single HTML file with JavaScript works.

## Key Insight

Start with the simplest version (single file). Add complexity only when needed.

---

[← Pipeline Pattern](08-pattern-pipeline.md) | [Next: Build Incrementally →](10-build-incrementally.md)
