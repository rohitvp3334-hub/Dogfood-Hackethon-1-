# 🏗 System Architecture – CyberShield

## 🔍 Overview
CyberShield is designed as a lightweight intrusion detection and alert system.  
It monitors logs, applies detection rules/ML models, and displays alerts on a dashboard.

---

## 📐 High-Level Architecture
1. **Log Collector**  
   - Collects system logs or simulated attack data.  
   - Input sources: server logs, network traffic, user activity.  

2. **Detection Engine**  
   - Rule-based detection (e.g., failed login threshold).  
   - Optional ML model for anomaly detection.  

3. **Database Layer (SQLite)**  
   - Stores logs and flagged alerts.  
   - Provides structured access for dashboard queries.  

4. **Dashboard (Streamlit)**  
   - Displays charts, alerts, and event lifecycle.  
   - Real-time visualization of suspicious activity.  

5. **Docker Setup**  
   - Ensures reproducible environment.  
   - `docker-compose up` starts seeded portal with demo data.

---

## 🔄 Workflow
- Logs → Detection Engine → Database → Dashboard → Alerts.  

---

## 🛡 Security Considerations
- Minimal data exposure.  
- Demo uses simulated attacks only.  
- Scalable to enterprise SIEM integration.
