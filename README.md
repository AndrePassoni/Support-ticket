# Support Tickets API

A lightweight RESTful API built entirely with pure Node.js (without external frameworks like Express) to manage support tickets. It features a custom routing system, query string parsing, and a built-in JSON file-based database for data persistence.

> Made with Rocketseat Fullstack course.

## 🚀 Features

- **Custom Router:** Built from scratch using native Node.js `http` module and Regular Expressions.
- **JSON Persistence:** Custom database class to read and write data to a local `db.json` file.
- **CRUD Operations:** Create, Read, Update, and Delete support tickets.
- **Status Management:** Specific endpoint to update a ticket's status to "closed" and add a solution.
- **Filtering:** List tickets dynamically with optional query parameter filtering.

## 💻 Technologies

- **Node.js** (Native modules: `http`, `crypto`, `fs/promises`)
- **JavaScript** (ES Modules)

## 📦 Getting Started

### Prerequisites

- Node.js installed on your machine (v18+ recommended).

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/AndrePassoni/Support-ticket.git
   ```

2. Navigate to the project folder:
   ```bash
   cd Support-ticket
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```
   *The server will start running on `http://localhost:3333`.*

## 🛣️ API Endpoints

Base URL: `http://localhost:3333`

### 1. Create a Ticket
- **Route:** `POST /tickets`
- **Body (JSON):**
  ```json
  {
    "equipment": "Monitor",
    "description": "The monitor suddenly turns off.",
    "user_name": "Maria"
  }
  ```
- **Response:** `201 Created`

### 2. List Tickets
- **Route:** `GET /tickets`
- **Query Parameters (Optional):** `?status=open` or `?status=closed`
- **Response:** `200 OK`
  ```json
  [
    {
      "id": "db819ea8-af0c-4f96-8ea7-cfd79a768095",
      "equipment": "Monitor",
      "description": "The monitor suddenly turns off.",
      "user_name": "Maria",
      "status": "open",
      "created_at": "2026-03-06T15:20:01.323Z",
      "updated_at": "2026-03-06T15:20:01.323Z"
    }
  ]
  ```

### 3. Update a Ticket
- **Route:** `PUT /tickets/:id`
- **Body (JSON):**
  ```json
  {
    "equipment": "Monitor 24 inches",
    "description": "The monitor suddenly turns off after 10 minutes."
  }
  ```
- **Response:** `200 OK`

### 4. Close a Ticket
- **Route:** `PATCH /tickets/:id/close`
- **Body (JSON):**
  ```json
  {
    "solution": "Replaced the power cable."
  }
  ```
- **Response:** `200 OK` *(Updates status to "closed" and adds the solution).*

### 5. Delete a Ticket
- **Route:** `DELETE /tickets/:id`
- **Response:** `200 OK`

## 📁 Project Structure

```text
src/
├── controllers/      # Route controllers (create, index, update, remove, updateStatus)
├── database/         # Custom database logic and db.json file
├── middleware/       # Handlers for JSON parsing and Route matching
├── routes/           # Route definitions and mapping
├── utils/            # Helper functions (Regex path parsers, Query extractors)
└── server.js         # Application entry point
```

---

<p align="center">
  Made with 💜 by <a href="https://github.com/AndrePassoni">André Passoni</a>
</p>