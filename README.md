# 🌳 BFHL Hierarchy Processing API

A Full Stack JavaScript project that builds and hosts a REST API (`POST /bfhl`) to process hierarchical node relationships, detect trees/cycles, validate input, and return structured insights with a frontend interface for interaction.

## 🚀 Features

- REST API using Node.js and Express
- Hierarchical tree construction
- Cycle detection in graphs
- Invalid input handling
- Duplicate edge detection
- Multi-tree support
- Depth calculation
- Interactive frontend to test API
- Responsive UI for result visualization

---

# 🛠 Tech Stack

## Backend
- JavaScript (Node.js)
- Express.js
- CORS
- Body Parser

## Frontend
- HTML5
- CSS3
- JavaScript (Vanilla / React optional)

## Deployment
- Vercel / Render / Railway

---

# 📂 Project Structure

```bash
bfhl-hierarchy-api/
│
├── backend/
│   ├── server.js
│   ├── package.json
│   ├── routes/
│   │    └── bfhlRoutes.js
│   ├── controllers/
│   │    └── hierarchyController.js
│   ├── services/
│   │    ├── graphService.js
│   │    ├── cycleDetection.js
│   │    └── validationService.js
│   └── utils/
│        └── helperFunctions.js
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── screenshots/
│    ├── ui-preview.png
│
└── README.md
```

---

# 🏗 System Architecture

```text
                ┌────────────────┐
                │   User Input    │
                └──────┬──────────┘
                       │
                       ▼
               ┌─────────────────┐
               │ Frontend Client │
               └──────┬──────────┘
                      │ API Request
                      ▼
               ┌─────────────────┐
               │ Express Server  │
               └──────┬──────────┘
                      │
      ┌───────────────┼────────────────┐
      ▼               ▼                ▼
Validation      Graph Builder      Cycle Detection
Module             Module             Module
      │               │                │
      └───────────────┴────────────────┘
                      │
                      ▼
               Structured JSON Response
```

---

# ⚙️ API Endpoint

## POST /bfhl

### Request

```json
{
 "data": ["A->B","A->C","B->D"]
}
```

### Response

```json
{
"user_id":"yourname_ddmmyyyy",
"email_id":"yourmail@example.com",
"college_roll_number":"xxxx",
"hierarchies":[
{
"root":"A",
"tree":{
"A":{
"B":{"D":{}},
"C":{}
}
},
"depth":3
}
],
"invalid_entries":[],
"duplicate_edges":[],
"summary":{
"total_trees":1,
"total_cycles":0,
"largest_tree_root":"A"
}
}
```

---

# 📌 Processing Rules Implemented

## Validation
Checks for:

✔ Correct format `X->Y`

✔ Uppercase letters only

✔ Self-loop rejection

✔ Empty input handling

✔ Invalid entries reporting

---

## Duplicate Handling
- First edge considered valid  
- Repeated edges stored in duplicate list

Example:

```text
A->B
A->B
A->B
```

Returns:

```text
Duplicate: A->B
```

---

## Cycle Detection
Example:

```text
X->Y
Y->Z
Z->X
```

Returns:

```json
{
"root":"X",
"tree":{},
"has_cycle":true
}
```

---

# ▶ Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/bfhl-hierarchy-api.git
cd bfhl-hierarchy-api
```

## Install Dependencies

```bash
npm install
```

## Run Server

```bash
npm start
```

Server runs at:

```bash
http://localhost:3000
```

---

# 💻 Run Frontend

Open:

```bash
frontend/index.html
```

or host using Live Server.

---

# 🧪 Testing Sample Input

```json
[
"A->B",
"A->C",
"B->D",
"X->Y",
"Y->Z",
"Z->X"
]
```

Expected:
- One valid tree
- One cycle detected

---

# 📈 Time Complexity

| Operation | Complexity |
|---------|-------------|
Validation | O(n) |
Graph Build | O(n) |
Cycle Detection | O(V+E) |
Depth Calculation | O(V+E) |

Efficient for up to 50+ nodes under 3 sec.

---

# 📷 UI Preview

Add screenshots here:

```md
![UI Screenshot](screenshots/ui-preview.png)
```

---

# 🔮 Future Enhancements

- Graph visualization using D3.js
- Drag and drop node builder
- Unit testing with Jest
- Docker deployment
- Authentication for API access

---

# 👨‍💻 Author

Your Name  
Roll No: XXXXX  
Email: yourmail@example.com

---

# 📜 License

This project is licensed under the MIT License.
