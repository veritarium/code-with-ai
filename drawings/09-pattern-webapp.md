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

## Reading This Drawing

**The Two-Layer Structure:** The main diagram shows web apps have two parts:

**FRONTEND (Top Layer):** What the user sees and interacts with in their browser.
- **Page:** The overall structure and layout
- **Form:** Where users enter data (input fields, buttons)
- **Display:** Where results and data are shown (tables, lists, charts)

**BACKEND (Bottom Layer):** The server-side code that does the work.
- **API Routes:** Entry points that receive requests (GET /items, POST /items)
- **Logic:** Business rules and calculations
- **Data Storage:** Where information is saved (database, files)

**Request/Response Arrow:** The connection between frontend and backend. User clicks a button → frontend sends request to backend → backend processes → backend sends response → frontend displays result.

**The Build Sequence:** Build bottom-up, not top-down. Start with what you can test independently:
1. **DATA:** Create storage first. "Create a function to store and retrieve items from a list"
2. **LOGIC:** Add operations. "Add functions: add_item, get_items, delete_item"
3. **API:** Expose logic via routes. "Create Flask routes: GET /items, POST /items, DELETE /items"
4. **FRONTEND:** Create the interface. "Create HTML page with form to add items and list to show them"
5. **CONNECT:** Wire frontend to backend. "Make form submit to API, refresh list on response"

Each step is testable before moving on.

**The Simple Version Box:** For many tools, you don't need a backend at all. A single HTML file with:
- **HTML:** Structure (what elements exist)
- **CSS:** Style (how it looks)
- **JavaScript:** Behavior (what happens when you click)

Using localStorage (browser storage), you can build functional tools without any server. Example prompt: "Create single HTML file with form, styled nicely, that stores data in browser localStorage"

## What This Shows

Web apps have frontend (what user sees) and backend (logic + data). Build bottom-up: data → logic → API → frontend → connect. For simple tools, a single HTML file with JavaScript works.

## Key Insight

Start with the simplest version (single file). Add complexity only when needed.

## What This Means In Practice

Ask yourself: Does this need a server?
- **No server needed:** Personal tools, calculators, single-user apps → Single HTML file
- **Server needed:** Multiple users, persistent data, secure operations → Full frontend + backend

When in doubt, start with a single file. You can always add a backend later if needed.

---

[← Pipeline Pattern](08-pattern-pipeline.md) | [Next: Build Incrementally →](10-build-incrementally.md)
