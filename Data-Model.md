# 🗂 Data Model – CyberShield

## 📊 Overview
CyberShield uses a lightweight SQLite database to store logs and alerts.  
This ensures fast queries and easy visualization.

---

## 🗄 Tables

### 1. Logs Table
| Field        | Type     | Description                          |
|--------------|----------|--------------------------------------|
| id           | INTEGER  | Unique identifier                    |
| timestamp    | DATETIME | Event time                           |
| source       | TEXT     | Source of log (server, app, network) |
| event_type   | TEXT     | Type of event (login, scan, etc.)    |
| status       | TEXT     | Success / Failed                     |

---

### 2. Alerts Table
| Field        | Type     | Description                          |
|--------------|----------|--------------------------------------|
| id           | INTEGER  | Unique identifier                    |
| log_id       | INTEGER  | Reference to Logs table              |
| alert_type   | TEXT     | Type of alert (brute force, phishing)|
| severity     | TEXT     | Low / Medium / High                  |
| message      | TEXT     | Human-readable alert message         |
| timestamp    | DATETIME | Alert time                           |

---

## 🔗 Relationships
- **Logs → Alerts**: Each alert references a suspicious log entry.  
- One log can generate multiple alerts if multiple rules are triggered.

---

## 📈 Example Data
**Logs Table**
| id | timestamp           | source   | event_type | status   |
|----|---------------------|----------|------------|----------|
| 1  | 2026-09-24 15:30:00 | server01 | login      | failed   |
| 2  | 2026-09-24 15:31:00 | server01 | login      | failed   |

**Alerts Table**
| id | log_id | alert_type   | severity | message                  | timestamp           |
|----|--------|--------------|----------|--------------------------|---------------------|
| 1  | 1      | brute_force  | High     | Multiple failed logins   | 2026-09-24 15:31:10 |
