[![Deploy to Cloudflare](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/smokindope/1-click-panel-test)


# TFMS TV Panel – Cloudflare Workers Edition



A lightweight IPTV / streaming panel built for **Cloudflare Workers + D1 Database**, designed for fast deployment and serverless hosting.

---

## 🚀 Features

* Cloudflare Workers backend (edge runtime)
* D1 SQLite database integration
* Streams management system
* Proxy support
* User authentication system
* Admin panel settings
* Automatic database initialization
* Fully serverless (no VPS required)

---

## 📦 Project Structure

```txt
project-root/
├── src/
│   └── worker.js
├── schema.sql
├── wrangler.jsonc
├── package.json
└── README.md
```

---

## 🛠️ Setup Instructions

### 1. Create Cloudflare Resources

You need:

* A **D1 Database**
* A **KV Namespace**

Create them in Cloudflare Dashboard:

* Workers & Pages → D1 → Create database
* Workers & Pages → KV → Create namespace

Copy IDs into `wrangler.jsonc`.

---

### 2. Configure `wrangler.jsonc`

```jsonc
{
  "name": "tfms-tv-panel",
  "main": "src/worker.js",
  "compatibility_date": "2026-05-29",

  "d1_databases": [
    {
      "binding": "DB",
      "database_name": "tfms-panel-db",
      "database_id": "YOUR_D1_ID"
    }
  ],

  "kv_namespaces": [
    {
      "binding": "KV_CONNECTIONS",
      "id": "YOUR_KV_ID"
    }
  ]
}
```

---

### 3. Deploy via One Click (No CLI Needed)

Click the button above to deploy instantly to Cloudflare Workers.

Or:

1. Push project to GitHub
2. Go to Cloudflare Dashboard
3. Workers & Pages → Create Application
4. Import Git Repository
5. Select repo
6. Click Deploy

---

## 🧠 Database Schema

Automatically created on first run:

### Tables

* `users` → login accounts
* `streams` → IPTV stream list
* `proxies` → proxy endpoints
* `comments` → admin notes
* `settings` → admin credentials

### Default Admin

```
username: admin
password: SecretPassword123
```

---

## ⚙️ How It Works

On every request:

1. Worker connects to D1
2. Auto-initializes database (if missing)
3. Routes request:

   * `/login` → authentication
   * `/streams` → stream list
   * `/playlist` → IPTV output
   * `/admin` → panel interface
   * `/proxy` → proxy handler

---

## 🔐 Security Notes

This project is **basic by default**. For production use:

* Change default admin password
* Hash passwords (recommended bcrypt or WebCrypto)
* Add session expiration
* Enable rate limiting
* Restrict proxy endpoints

---

## ⚡ Performance

* Runs at Cloudflare edge globally
* No server maintenance
* Instant scaling
* Low-latency API responses

---

## 🧪 Development

Run locally:

```
npm install
npm run dev
```

Deploy:

```
npm run deploy
```

---

## 📌 Notes

* Database auto-creates tables on first request
* No manual SQL import required (if bootstrap is enabled)
* KV is used for connection/session tracking

---

## 📄 License

Use responsibly. Modify freely for personal or internal projects.
