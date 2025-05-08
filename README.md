# 🐍 Hydra – Network Login Cracker

Hydra is a fast and flexible **brute-forcing tool** used to test login credentials across a wide range of network services. It supports both **CLI and GUI** (via xHydra), making it suitable for both quick tests and large-scale automated attacks.

---

## 🧪 Two Hydra Syntax Styles

Hydra supports two styles for writing commands. Both achieve the same goal, but the newer style is more consistent and easier to script.

**Example: Brute-force SSH on `192.168.1.100` with port `2222`:**

- **Old Style:**
  ```bash
  hydra -L users.txt -P pass.txt -s 2222 192.168.1.100 ssh
- **New Style:**
  ```bash
  hydra ssh://192.168.1.100:2222 -L users.txt -P pass.txt

⚙️ Common Hydra Options
Option	Description
- -l <username>	Use a single username
- -L <filename>	Use a file containing a list of usernames
- -p <password>	Use a single password
- -P <filename>	Use a file containing a list of passwords
- -C <filename>	Use a file with username:password pairs
- -M <filename>	Use a file with target IP addresses
- -R	Restore a previous session
- -s <port>	Specify a target port
- -e nsr	Try null password (n), username as password (s), and reversed username (r)
- -V	Verbose mode — show each attempt
- -o <file>	Save output to a file

📝 Note:

Both IP addresses and CIDR subnets can be used as targets.

Target lists can vary based on whether services run on the same port or different ports.

## 🧩 Supported Protocols

Hydra supports a wide range of protocols for brute-force authentication. These are categorized below:

---

### 🔐 Authentication / Remote Access

| Protocol             | Description                                                  |
|----------------------|--------------------------------------------------------------|
| `cisco / cisco-enable` | Cisco device login / enable password brute-force            |
| `ssh`                | Secure Shell remote login (encrypted)                        |
| `telnet(s)`          | Telnet protocol (unencrypted)                                |
| `rlogin`             | Unix remote login (deprecated)                               |
| `rdp`                | Windows Remote Desktop                                       |
| `vnc`                | Virtual Network Computing for GUI remote access              |

---

### 🌐 Web Services

| Protocol                        | Description                                             |
|---------------------------------|---------------------------------------------------------|
| `http(s)-head/get/post`        | Basic HTTP/HTTPS requests                               |
| `http(s)-[get|post]-form`      | Brute-force web login forms                             |
| `http-proxy`                   | Login attempts on proxy servers                         |
| `http-proxy-urlenum`           | Enumerate usernames via proxy URLs                      |

**Example for HTTP POST login form:**
```bash
hydra 192.168.1.100 http-post-form "/login.php:username=^USER^&password=^PASS^&submitbtn=Submit:The username or password is not correct. Please try again" -L users.txt -P pass.txt -V -f
```
---

### 📂 File Transfer Protocols

| Protocol   | Description                                         |
|------------|-----------------------------------------------------|
| `ftp(s)`   | File Transfer Protocol, optionally over SSL/TLS     |

---

### 💬 Messaging / Communication

| Protocol | Description                |
|----------|----------------------------|
| `irc`    | Internet Relay Chat        |
| `icq`    | Instant Messaging (legacy) |

---

### 🛡️ Network Services

| Protocol   | Description                                               |
|------------|-----------------------------------------------------------|
| `smb`      | Windows file/printer sharing                              |
| `snmp`     | Network device management (often via guessable community strings) |
| `sip`      | VoIP signaling protocol                                   |
| `ldap2(s)` | Lightweight Directory Access Protocol (with/without SSL)  |

---

### ✉️ Email Services

| Protocol   | Description                        |
|------------|------------------------------------|
| `imap(s)`  | Internet Message Access Protocol (secure) |
| `smtp`     | Simple Mail Transfer Protocol (sending email) |
| `pop3(s)`  | Post Office Protocol (legacy email retrieval) |

---

### 🧠 Database Services

| Protocol   | Description                                  |
|------------|----------------------------------------------|
| `mysql`    | MySQL — open-source relational database      |
| `mssql`    | Microsoft SQL Server                         |
| `postgres` | PostgreSQL — advanced open-source RDBMS      |

---
