# 🤖 Full-Stack AI ChatBot

A modern, scalable **Full-Stack AI Chatbot Application** built with **React, Node.js, Express, and MongoDB**.

The application supports multiple Large Language Models (LLMs), allowing users to interact with **OpenAI, Google Gemini, and Groq** from a single, unified chatbot interface.

It also provides secure authentication, persistent chat history, Markdown rendering, syntax-highlighted code responses, typing indicators, and a modern responsive UI.

---

## ✨ Features

### 🤖 Multi-LLM AI Support

Switch between multiple AI providers from the same application:

* 🟢 **OpenAI**
* 🔵 **Google Gemini**
* 🟠 **Groq**
* 🔄 Provider/model switching
* ⚡ Fast AI responses
* 🛡️ Backend-side API key protection
* 🧩 Extensible architecture for adding future LLM providers

### 💬 Advanced Chat Experience

* Real-time typing indicator
* Chat history
* New conversation support
* Markdown response rendering
* Code syntax highlighting
* Copy code functionality
* Emoji picker
* User/AI message differentiation
* Loading states
* Error handling
* Responsive chat layout

### 🔐 Authentication & Security

* User registration
* User login
* JWT authentication
* Password hashing with bcrypt
* Protected API routes
* User-specific chat history
* Backend environment variable protection

### 🎨 Modern UI/UX

Built with a combination of:

* React
* Tailwind CSS
* Material UI
* Lucide React
* Responsive layouts
* Modern chat components
* Interactive buttons and controls
* Clean dashboard experience

### 💾 Persistent Chat History

Chat conversations are stored in MongoDB, allowing users to:

* Create conversations
* Continue previous conversations
* Store AI responses
* Store user messages
* Retrieve chat history
* Maintain user-specific conversations

---

# 🏗️ Application Architecture

```text
┌───────────────────────────────┐
│        React + Vite           │
│                               │
│  Chat UI                      │
│  Authentication               │
│  Markdown Renderer             │
│  Code Highlighting             │
└───────────────┬───────────────┘
                │
                │ REST API
                ▼
┌───────────────────────────────┐
│       Node.js + Express       │
│                               │
│  Authentication               │
│  Chat APIs                    │
│  AI Provider Services          │
│  JWT Middleware                │
│  Error Handling               │
└───────┬───────────┬───────────┘
        │           │
        │           │
        ▼           ▼
┌─────────────┐  ┌──────────────────────┐
│  MongoDB    │  │      AI Providers    │
│             │  │                      │
│ Users       │  │ OpenAI               │
│ Chats       │  │ Gemini               │
│ Messages    │  │ Groq                 │
└─────────────┘  └──────────────────────┘
```

---

# 🧠 AI Provider Architecture

The backend uses a provider-based approach so AI services can be switched without changing the frontend.

```text
                    User
                     │
                     ▼
               Chat Request
                     │
                     ▼
              Express API
                     │
                     ▼
             AI Provider Layer
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
     OpenAI       Gemini         Groq
        │            │            │
        └────────────┼────────────┘
                     ▼
                AI Response
                     │
                     ▼
                MongoDB
                     │
                     ▼
                  Client
```

This makes the application easier to maintain and extend with additional providers in the future.

---

# 🛠️ Tech Stack

## Frontend

| Technology               | Purpose                   |
| ------------------------ | ------------------------- |
| React 19                 | UI development            |
| Vite                     | Development/build tooling |
| React Router DOM         | Client-side routing       |
| Tailwind CSS             | Utility-first styling     |
| Material UI              | UI components             |
| Lucide React             | Icons                     |
| Axios                    | HTTP requests             |
| React Markdown           | Markdown rendering        |
| React Syntax Highlighter | Code highlighting         |
| Emoji Picker React       | Emoji support             |
| clsx                     | Conditional classes       |
| tailwind-merge           | Tailwind class merging    |

## Backend

| Technology           | Purpose                   |
| -------------------- | ------------------------- |
| Node.js              | Runtime                   |
| Express.js           | REST API                  |
| MongoDB              | Database                  |
| Mongoose             | MongoDB ODM               |
| JWT                  | Authentication            |
| bcryptjs             | Password hashing          |
| OpenAI SDK           | OpenAI integration        |
| Google Generative AI | Gemini integration        |
| Groq SDK             | Groq integration          |
| dotenv               | Environment configuration |

---

# 📁 Project Structure

```text
LLM-Model/
│
├── Frontend/
│   │
│   ├── public/
│   │
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── context/
│   │   ├── utils/
│   │   ├── App.jsx
│   │   └── main.jsx
│   │
│   ├── package.json
│   └── vite.config.js
│
├── Server/
│   │
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   │   ├── openai/
│   │   ├── gemini/
│   │   └── groq/
│   │
│   ├── utils/
│   ├── config/
│   ├── server.js
│   ├── package.json
│   └── .env
│
├── .gitignore
└── README.md
```

---

# 🔄 Chat Request Flow

When a user sends a message:

```text
1. User enters message
          ↓
2. Frontend sends API request
          ↓
3. JWT authentication middleware
          ↓
4. Backend validates request
          ↓
5. Selected AI provider is identified
          ↓
6. Request sent to OpenAI/Gemini/Groq
          ↓
7. AI generates response
          ↓
8. Response returned to backend
          ↓
9. Conversation saved in MongoDB
          ↓
10. Response returned to React
          ↓
11. UI displays formatted response
```

---

# 🔐 Authentication Flow

```text
Register
   │
   ▼
Validate User
   │
   ▼
Hash Password
   │
   ▼
Save User → MongoDB
   │
   ▼
Login
   │
   ▼
Verify Password
   │
   ▼
Generate JWT
   │
   ▼
Frontend stores authentication state
   │
   ▼
Protected API Requests
```

---

# 🚀 Getting Started

## Prerequisites

Make sure you have installed:

* Node.js 18+
* npm
* MongoDB or MongoDB Atlas
* Git

You also need at least one AI provider API key:

* OpenAI
* Google Gemini
* Groq

---

# 📥 Installation

## 1. Clone Repository

```bash
git clone https://github.com/adityadhar16/LLM-Model.git

cd LLM-Model
```

---

# ⚙️ Backend Setup

Navigate to the backend:

```bash
cd Server
```

Install dependencies:

```bash
npm install
```

Create:

```text
Server/.env
```

Add:

```env
PORT=5000

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_secure_jwt_secret

OPENAI_API_KEY=your_openai_api_key

GEMINI_API_KEY=your_gemini_api_key

GROQ_API_KEY=your_groq_api_key
```

Start development server:

```bash
npm run dev
```

Backend should run on:

```text
http://localhost:5000
```

---

# 💻 Frontend Setup

Open another terminal:

```bash
cd Frontend
```

Install dependencies:

```bash
npm install
```

Create:

```text
Frontend/.env
```

Example:

```env
VITE_API_URL=http://localhost:5000
```

Start the frontend:

```bash
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

# 🔑 Environment Variables

## Backend

```env
PORT=5000
MONGO_URI=
JWT_SECRET=

OPENAI_API_KEY=
GEMINI_API_KEY=
GROQ_API_KEY=
```

## Frontend

```env
VITE_API_URL=http://localhost:5000
```

> ⚠️ Never expose AI provider API keys in frontend environment variables. Keep them on the backend.

---

# 🤖 Gemini Model Configuration

If you are using the newer Gemini API/models, keep the model name configurable rather than hard-coding it throughout the application.

For example:

```env
GEMINI_MODEL=gemini-3.6-flash
```

Backend:

```js
const modelName =
  process.env.GEMINI_MODEL || "gemini-3.6-flash";
```

This makes future model migrations much easier.

---

# 🔌 API Structure

Example API organization:

```text
/api
│
├── /auth
│   ├── POST /register
│   └── POST /login
│
├── /chat
│   ├── POST /
│   ├── GET /
│   ├── GET /:id
│   └── DELETE /:id
│
└── /users
    └── GET /profile
```

---

# 🧾 Example Chat Request

```json
{
  "message": "Explain React hooks",
  "provider": "gemini"
}
```

Example response:

```json
{
  "success": true,
  "message": "React Hooks allow functional components to use state and other React features.",
  "provider": "gemini"
}
```

---

# 🗄️ MongoDB Data Model

A typical conversation structure:

```text
User
 │
 ├── name
 ├── email
 ├── password
 └── conversations
       │
       ├── title
       ├── provider
       ├── createdAt
       └── messages
             ├── role
             ├── content
             └── timestamp
```

Example message:

```json
{
  "role": "user",
  "content": "What is Node.js?",
  "timestamp": "2026-09-04T10:00:00Z"
}
```

---

# 🛡️ Security

The application follows several security practices:

* Password hashing using bcrypt
* JWT-based authentication
* Protected backend routes
* Environment variables for secrets
* User-specific chat access
* Server-side AI API calls
* Input validation
* Error handling
* `.env` excluded from Git

Add to `.gitignore`:

```gitignore
node_modules/
.env
.env.local
dist/
build/
```

---

# ⚡ Error Handling

The application handles common failures such as:

```text
❌ Invalid credentials
❌ Unauthorized request
❌ MongoDB connection failure
❌ Invalid AI provider
❌ AI API failure
❌ Missing API key
❌ Rate limit exceeded
❌ Invalid request
```

A provider failure should return a controlled error rather than exposing internal API details to the client.

---

# 🧪 Testing Checklist

Before deployment, verify:

### Authentication

* [ ] User registration
* [ ] Duplicate email validation
* [ ] Login
* [ ] Invalid password
* [ ] JWT validation
* [ ] Logout

### Chat

* [ ] Send message
* [ ] Receive AI response
* [ ] Loading state
* [ ] Typing indicator
* [ ] Markdown
* [ ] Code blocks
* [ ] Copy code
* [ ] Chat history

### AI Providers

* [ ] OpenAI
* [ ] Gemini
* [ ] Groq
* [ ] Invalid API key handling
* [ ] Rate-limit handling
* [ ] Provider failure handling

### Database

* [ ] MongoDB connection
* [ ] User creation
* [ ] Chat creation
* [ ] Message persistence
* [ ] Chat retrieval
* [ ] Chat deletion

---

# 📸 Screenshots

Add your application screenshots here:

```text
docs/
├── login.png
├── signup.png
├── chat-dashboard.png
├── model-selection.png
└── chat-history.png
```

Example:

```md
## 📸 Screenshots

### Login

![Login](./docs/login.png)

### AI Chat

![AI Chat](./docs/chat-dashboard.png)

### Model Selection

![Model Selection](./docs/model-selection.png)
```

---

# 🚀 Future Improvements

Planned features:

* [ ] Streaming AI responses
* [ ] Voice input
* [ ] Text-to-speech
* [ ] PDF upload
* [ ] PDF question answering
* [ ] RAG pipeline
* [ ] Vector database
* [ ] Conversation search
* [ ] AI-generated conversation titles
* [ ] Image generation
* [ ] File attachments
* [ ] Web search
* [ ] Multi-modal AI
* [ ] Admin dashboard
* [ ] Usage analytics
* [ ] Rate limiting
* [ ] Redis caching
* [ ] Docker deployment
* [ ] CI/CD pipeline

---

# 🧠 Future RAG Architecture

The chatbot can be extended into a production-ready **PDF/RAG AI assistant**:

```text
                 PDF Upload
                     │
                     ▼
                PDF Parser
                     │
                     ▼
                 Text Split
                     │
                     ▼
                Embeddings
                     │
                     ▼
              Vector Database
                     │
User Question ───────┤
                     ▼
                 Retriever
                     │
                     ▼
              Relevant Context
                     │
                     ▼
                 LLM Model
                     │
                     ▼
              Generated Answer
```

Potential technologies:

```text
Next.js / React
Node.js
PostgreSQL / MongoDB
Vector DB
Redis
OpenAI / Gemini / Groq
Docker
```

---

# 📈 Production Improvements

For production deployment, consider:

### Performance

* Response streaming
* Redis caching
* Database indexing
* Connection pooling
* Request timeouts

### Scalability

* Load balancing
* Background jobs
* Queue-based processing
* Horizontal scaling
* Stateless API architecture

### Security

* Rate limiting
* Helmet
* CORS configuration
* Input sanitization
* API request validation
* Secret management
* Refresh-token strategy

### Monitoring

* Structured logging
* Error tracking
* API metrics
* AI token/cost tracking
* Database monitoring

---

# 🐳 Docker

A future production setup can use:

```text
Docker Compose
│
├── Frontend
├── Backend
├── MongoDB
└── Redis
```

Example:

```bash
docker compose up -d
```

---

# 🤝 Contributing

Contributions, issues, and feature requests are welcome.

### Steps

```bash
git checkout -b feature/my-feature

git add .

git commit -m "feat: add my feature"

git push origin feature/my-feature
```

Then create a Pull Request.

---

# 📄 License

This project is available for educational and development purposes.

---

# 👨‍💻 Author

**Aditya**

Full-Stack / MERN Developer

### Focus Areas

```text
React
Next.js
Node.js
Express
MongoDB
PostgreSQL
AI Integration
Generative AI
RAG
REST APIs
Docker
```

---

# ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

**Happy Coding! 🚀🤖**
#   l l m _ m o d e l 2  
 