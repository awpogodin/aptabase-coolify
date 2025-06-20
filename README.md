# Aptabase Docker Compose for Coolify

🚀 Ready-to-use `docker-compose.yml` to deploy [Aptabase](https://aptabase.com/) on [Coolify](https://coolify.io).

This configuration sets up:

- PostgreSQL (for main data)
- ClickHouse (for event analytics)
- Aptabase (analytics frontend/backend)

All services are pre-configured and ready to be used behind Coolify's proxy with Let's Encrypt support.

---

## ✅ Requirements

- [Coolify](https://coolify.io) installed and configured
- Domain name pointing to your server IP
- Docker & Docker Compose (if running locally)

---

## 🚀 How to Use

1. **Create a new application in Coolify:**

   - Go to **Create Resource → Docker Compose Empty**
   - Choose your server
   - Paste the contents of this repo's `docker-compose.yml` file

2. **Set environment variables in Coolify UI:**

| Variable                      | Description                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| `SERVICE_USER_POSTGRES`       | PostgreSQL username (e.g., `aptabase`)                       |
| `SERVICE_PASSWORD_POSTGRES`   | PostgreSQL password                                          |
| `SERVICE_USER_CLICKHOUSE`     | ClickHouse username                                          |
| `SERVICE_PASSWORD_CLICKHOUSE` | ClickHouse password                                          |
| `SERVICE_BASE64_APTABASE`     | Auth secret key ([generate here](https://randomkeygen.com/)) |
| `SERVICE_FQDN_APTABASE`       | Your domain (e.g., `aptabase.example.com`)                   |

> 💡 All variables are pre-filled by **Coolify's magic environment variables**. You can leave them as-is if you're okay with the defaults.

3. Click **Deploy**

---

## 🔐 First Login Instructions

Since SMTP is not configured by default, Aptabase will generate an activation link that you need to find manually:

1. After deployment, go to **Logs → Aptabase container**
2. Search for a link like this one:

https://aptabase-xxxx.yourdomain.com/api/_auth/continue?token=xxxx

3. Open the link in your browser to complete registration
