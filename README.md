
# Passbolt Docker Compose Setup

This project sets up a production-ready Passbolt instance using Docker Compose. It includes Passbolt CE, MariaDB, and NGINX as a reverse proxy.

## 🧱 Project Structure

- `passbolt-db`: MariaDB container for storing secrets.
- `passbolt`: Passbolt CE container.
- `nginx`: Acts as a reverse proxy for HTTP routing.

## 🔐 Environment Variables

Environment variables are configured in the `.env` file. All sensitive values should be injected securely using Vault placeholders (e.g., `[VAULT_INJECTED_SECRET]`).

## 📁 How to Use

### 1. Clone the Repo
```bash
git clone <repo-url>
cd <repo-folder>
```

### 2. Set Up `.env`
Create a `.env` file (sample provided) and populate it. Vault will inject secrets in production.

### 3. Start Containers
```bash
docker-compose up -d --build
```

### 4. Access Passbolt
Visit: `http://localhost` (or via your NGINX Proxy Manager / wildcard domain).

## 📦 Volumes

- `db_data`: Stores MariaDB database files.
- `gpg_volume`: Stores GPG keys for Passbolt.

## 📡 Network

All services are connected to a single bridge network: `passbolt_net`.

## ⚠️ Notes

- TLS/SSL termination is expected to be handled by an external reverse proxy (e.g., NGINX Proxy Manager or Load Balancer).
- This setup assumes you are deploying behind an existing secure HTTPS layer.

## 📄 License

MIT License
