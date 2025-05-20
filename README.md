# Goof - Snyk's vulnerable demo app

A vulnerable Node.js demo application for experimenting with known security vulnerabilities.

## How to Run

1. Start MongoDB:
```bash
mongod &
```

2. Clone the repo and install dependencies:
```bash
git clone https://github.com/snyk-labs/nodejs-goof
cd nodejs-goof
npm install
```

3. Start the app:
```bash
npm start
```

The app will run locally at http://localhost:3001

---

## Key Vulnerabilities

- Known vulnerable npm packages (e.g. mongoose, marked)
- NoSQL Injection in login
- Code Injection in account details
- Open Redirects
- Cross-site Scripting (XSS)
- Hardcoded secrets and insecure configs

---

## How to Test Vulnerabilities

Try sending malicious payloads to the `/login` and `/account_details` endpoints as described in the full documentation.

---

## Fixing Vulnerabilities

Use Snyk to test and fix:

```bash
npm install -g snyk
snyk test
snyk wizard
```

---

## Additional Info

- Supports Docker and Docker Compose
- Compatible with older MongoDB versions (MongoDB 3 recommended)

---

For detailed info, see the full documentation in this repository.
