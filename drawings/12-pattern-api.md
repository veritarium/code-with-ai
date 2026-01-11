# 12: Pattern — API

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                            PATTERN: API                                      ║
║                                                                              ║
║   Use this pattern when: Systems need to talk to each other                  ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │          REQUEST                              RESPONSE               │    ║
║  │                                                                      │    ║
║  │   ┌──────────┐      ┌──────────────────┐      ┌──────────┐          │    ║
║  │   │          │      │                  │      │          │          │    ║
║  │   │  CLIENT  │─────►│       API        │─────►│  CLIENT  │          │    ║
║  │   │          │      │                  │      │          │          │    ║
║  │   │ "I want  │      │  Receives,       │      │ "Here's  │          │    ║
║  │   │  data X" │      │  Processes,      │      │  data X" │          │    ║
║  │   │          │      │  Returns         │      │          │          │    ║
║  │   └──────────┘      └──────────────────┘      └──────────┘          │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   THE FOUR OPERATIONS (CRUD):                                                ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌────────────┬────────────┬────────────────────────────────────┐ │    ║
║   │   │  ACTION    │   METHOD   │   EXAMPLE                          │ │    ║
║   │   ├────────────┼────────────┼────────────────────────────────────┤ │    ║
║   │   │  Create    │   POST     │   POST /items      → Add new item  │ │    ║
║   │   │  Read      │   GET      │   GET /items       → List items    │ │    ║
║   │   │            │            │   GET /items/5     → Get item 5    │ │    ║
║   │   │  Update    │   PUT      │   PUT /items/5     → Replace item  │ │    ║
║   │   │  Delete    │   DELETE   │   DELETE /items/5  → Remove item   │ │    ║
║   │   └────────────┴────────────┴────────────────────────────────────┘ │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   API STRUCTURE:                                                             ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │                        ┌──────────────────┐                         │    ║
║   │                        │      ROUTER      │                         │    ║
║   │                        │                  │                         │    ║
║   │                        │  /items ──────┐  │                         │    ║
║   │                        │  /users ────┐ │  │                         │    ║
║   │                        │  /orders ─┐ │ │  │                         │    ║
║   │                        └───────────┼─┼─┼──┘                         │    ║
║   │                                    │ │ │                            │    ║
║   │                    ┌───────────────┘ │ └───────────────┐            │    ║
║   │                    │                 │                 │            │    ║
║   │                    ▼                 ▼                 ▼            │    ║
║   │             ┌──────────┐      ┌──────────┐      ┌──────────┐        │    ║
║   │             │  Order   │      │   User   │      │   Item   │        │    ║
║   │             │ Handler  │      │ Handler  │      │ Handler  │        │    ║
║   │             └────┬─────┘      └────┬─────┘      └────┬─────┘        │    ║
║   │                  │                 │                 │              │    ║
║   │                  └────────────┬────┴─────────────────┘              │    ║
║   │                               │                                     │    ║
║   │                               ▼                                     │    ║
║   │                        ┌──────────────┐                             │    ║
║   │                        │     DATA     │                             │    ║
║   │                        │   STORAGE    │                             │    ║
║   │                        └──────────────┘                             │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE:                                                            ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. DATA                                                           │    ║
║   │      "Create list to store items in memory"                         │    ║
║   │                                                                     │    ║
║   │   2. ONE ENDPOINT                                                   │    ║
║   │      "Create GET /items that returns all items as JSON"             │    ║
║   │                                                                     │    ║
║   │   3. TEST IT                                                        │    ║
║   │      "Start the server and test with curl"                          │    ║
║   │                                                                     │    ║
║   │   4. ADD ENDPOINTS                                                  │    ║
║   │      "Add POST /items to create new item"                           │    ║
║   │      "Add GET /items/{id} to get single item"                       │    ║
║   │      "Add DELETE /items/{id} to remove item"                        │    ║
║   │                                                                     │    ║
║   │   5. ADD VALIDATION                                                 │    ║
║   │      "Validate that item has name and price before creating"        │    ║
║   │                                                                     │    ║
║   │   6. ADD ERROR RESPONSES                                            │    ║
║   │      "Return 404 if item not found, 400 if invalid data"            │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   CONSUMING AN API (using someone else's):                                   ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. "Fetch data from https://api.example.com/items"                │    ║
║   │   2. "Parse the JSON response and extract names"                    │    ║
║   │   3. "Handle errors if request fails"                               │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Request/Response Flow (Top):** The fundamental pattern of all APIs:
- **CLIENT sends REQUEST:** "I want data X" — A request goes to the API
- **API processes:** Receives, validates, computes, retrieves
- **CLIENT receives RESPONSE:** "Here's data X" — The result comes back

This is a conversation. Client asks, API answers.

**The CRUD Table:** Four operations handle everything in any API:
- **Create (POST):** Add new things. `POST /items` creates a new item
- **Read (GET):** Retrieve things. `GET /items` lists all items; `GET /items/5` gets item #5
- **Update (PUT):** Change things. `PUT /items/5` updates item #5
- **Delete (DELETE):** Remove things. `DELETE /items/5` removes item #5

The pattern: METHOD + path = operation. This is the universal language of web APIs.

**API Structure Diagram:** How requests flow through an API:
- **ROUTER:** The traffic director. Looks at the path (`/items`, `/users`, `/orders`) and sends each request to the right handler
- **HANDLERS:** The workers. Each handles one type of resource (Item Handler, User Handler, Order Handler)
- **DATA STORAGE:** Where information lives. All handlers share access to storage

The flow: Request → Router → Handler → Data → Handler → Response

**The Build Sequence:** How to construct an API:
1. **DATA:** Create storage. "Create list to store items in memory"
2. **ONE ENDPOINT:** Start simple. "Create GET /items that returns all items as JSON"
3. **TEST IT:** Verify it works. "Start the server and test with curl"
4. **ADD ENDPOINTS:** Expand CRUD operations one at a time
5. **ADD VALIDATION:** Protect the data. "Validate that item has name and price before creating"
6. **ADD ERROR RESPONSES:** Handle problems gracefully. "Return 404 if item not found, 400 if invalid data"

**Consuming an API (Bottom Box):** When you're using someone else's API:
1. Fetch data from the URL
2. Parse the response (usually JSON)
3. Handle errors if the request fails

Three prompts to use any external API.

## What This Shows

API = Request → Process → Response. Four operations cover everything: Create (POST), Read (GET), Update (PUT), Delete (DELETE). Router directs requests to handlers. Handlers access data.

## Key Insight

Every API is just CRUD operations on resources. Start with one GET endpoint, test it, then add the rest.

## What This Means In Practice

Building an API:
- Think "what resources do I have?" (items, users, orders)
- Each resource gets CRUD endpoints
- Build GET first (easiest to test), then POST, PUT, DELETE
- Test each endpoint before moving to the next

Using an API:
- Read the documentation to find endpoints
- Start with a simple GET request
- Add error handling once the basic flow works

---

[← Automation Pattern](11-pattern-automation.md) | [Next: Debugging Pattern →](13-pattern-debugging.md)
