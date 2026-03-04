# X-UI Traffic Control 🚀

A lightweight, real-time traffic monitoring dashboard designed specifically for **x-ui** (V2Ray/Xray) access logs. It visualizes connections, identifies services via a custom Knowledge Base, and helps filter out noise for better server security and management.

---

## ✨ Features

* **Real-time Streaming**: Live log updates using WebSockets and `tail -F`.
* **Consecutive Grouping**: Automatically collapses identical sequential requests into a single row with a counter (e.g., `×42`) to reduce visual clutter.
* **Knowledge Base**: 
    * Map obscure IPs/Domains to human-readable service names (e.g., `1.1.1.1` → `Cloudflare DNS`).
    * Filter out "Noise" by adding domains to an Ignore List.
    * Full CRUD (Create, Read, Update, Delete) support for rules directly from the UI.
* **Advanced Filtering**: 
    * Filter logs by specific Client Email.
    * "Unknown Only" toggle to focus exclusively on unidentified traffic.
* **Smart Analysis**: Integrated Whois/IP lookup via Check-Host for quick investigation of suspicious activity.
* **Modern UI**: High-performance dashboard built with Tailwind CSS, featuring a persistent **Dark Mode**.

---

## 🛠 Tech Stack

- **Backend**: Python 3.10+, FastAPI, Uvicorn, Asyncio.
- **Frontend**: HTML5, Vanilla JavaScript, Tailwind CSS.
- **Data**: JSON-based rule storage, Linux `tail` process integration.

---

## 🚀 Installation & Setup

Ensure you have Python installed on your server:
```bash
python3 --version
```

Ensure you have logs enabled 

### 1. Put serverexp.py and rules.json on your server
### 2. Install dependencies
```bash
pip3 install fastapi uvicorn websockets pydantic
```
### 3. Configure log path
Before running, ensure the `LOG_FILE_PATH` in `server.py` points to your actual x-ui access log:
`LOG_FILE_PATH = "/usr/local/x-ui/access.log"`

### 4. Download clientexp.html

---

## 🖥 Usage

### Start the Backend

You can use any method to start, but I prefer uvicorn

```bash
uvicorn server:app --host 0.0.0.0 --port 8000
```

### Open the Dashboard
Simply open `monitor.html` in any modern web browser.
1. Enter your server's **IP:Port** in the header.
2. Click **Connect**.
3. Use the **+** button on any log entry to categorize it or look it up.

---

## 📸 Interface Preview

<img width="2512" height="1256" alt="image" src="https://github.com/user-attachments/assets/5bdd1b79-6701-41e6-9d97-4177336ebf33" />

---

## 🛡 Security Note
This tool is intended for personal use. Ensure that your API port is protected by a firewall or bound to `127.0.0.1` if you are using an SSH tunnel/reverse proxy, as it exposes log data and rule configuration.

---

## 📄 License

MIT
