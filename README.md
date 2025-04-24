FastAPI Backend with JWT Auth, MongoDB & CI/CD Testing

✨ FastAPI Backend with JWT Auth, MongoDB & CI/CD Testing

Welcome to your complete **FastAPI backend template** that includes:

✅ REST API with FastAPI
🔐 JWT Authentication
🛢️ MongoDB integration
🧪 Automated Testing with `pytest`
⚙️ CI/CD Pipeline with GitHub Actions

---

📁 Project Structure


.
├── apiserver.py               # Core API endpoints (math operations)
├── main.py                    # Authentication & protected routes
├── auth.py                    # JWT handling & password hashing
├── db.py                      # MongoDB client connection
├── testAutomation.py          # Basic test script with requests
├── testAutomationPytest.py    # Parametrized test suite with pytest
└── .github/workflows/test.yml # CI/CD pipeline config (to be created)


---

🚀 Getting Started

🔧 Requirements


pip install fastapi uvicorn requests pytest     python-jose[cryptography] passlib[bcrypt] motor


▶️ Run the API Server


python apiserver.py


Browse to: [http://localhost:8000](http://localhost:8000)

---

🧮 API Features

🔢 Math Operations

| Endpoint        | Method | Description              |
|-----------------|--------|--------------------------|
| `/add/{x}/{y}`      | GET    | Returns `x + y`             |
| `/subtract/{x}/{y}` | GET    | Returns `x - y`             |
| `/multiply/{x}/{y}` | GET    | Returns `x * y`             |

Example: `GET http://localhost:8000/add/3/4 → {"result": 7}`

---

🔐 Auth with JWT (JSON Web Tokens)

📝 Register


POST /register?username=test&password=1234


🔑 Login to Get Token


POST /token


**Body (form):**

username=test
password=1234


🔒 Secure Route


GET /secure-data


**Headers:**

Authorization: Bearer <your_token>


Returns protected content only if the token is valid!

---

🧪 Testing

✅ Run Manual Tests


python testAutomation.py


🧪 Run Pytest Suite


pytest testAutomationPytest.py


Each test checks expected outputs from API endpoints with automatic assertion and reporting.

---

🔁 GitHub Actions CI/CD

📦 Automate Tests on Push

Create `.github/workflows/test.yml`:


name: 🧪 FastAPI API Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: ⬇️ Checkout Repository
        uses: actions/checkout@v2

      - name: 🐍 Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.10'

      - name: 📦 Install Dependencies
        run: |
          pip install fastapi uvicorn pytest requests \
              python-jose[cryptography] passlib[bcrypt] motor

      - name: 🚀 Start FastAPI Server
        run: nohup python apiserver.py &
        env:
          PYTHONUNBUFFERED: 1

      - name: ⏳ Wait for Server
        run: sleep 5

      - name: ✅ Run Tests
        run: pytest testAutomationPytest.py


Push to GitHub and check results in the **Actions** tab.

---

📈 Future Enhancements

•	- 🔄 Refresh tokens & logout functionality
•	- 🧰 Full database CRUD APIs
•	- 🔐 OAuth2 / API Key-based permissions
•	- 📊 Logging with ELK / CloudWatch
•	- ⚡ Load testing with `locust.io` or `pytest-benchmark`

---

👩‍💻 Author

Built with ❤️ by [Your Name](https://github.com/PrakritiRawat)

Contributions welcome! Feel free to fork and submit a PR.

---

📜 License

This project is licensed under the MIT License.


