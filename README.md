# ⚙️ DESH-QSI — Backend

> The detection engine, self-healing agent, and decentralized audit system powering the **DESH-QSI Decentralized AI Threat Intelligence System** — achieving 99.2% threat detection accuracy with sub-50ms response time and autonomous incident resolution in 8.3 seconds.

This is the backend repository. For the dashboard UI, see 👉 [desh-ai-frontend](https://github.com/DivekManan/desh-ai-frontend)

---

## 🔍 What Is DESH-QSI?

DESH-QSI (Decentralized Enhanced Security Hub — Quantum Security Intelligence) is a next-generation AI threat intelligence system that goes beyond traditional rule-based detection. Instead of relying on static signatures, it uses graph-based learning to model relationships between network entities and catch threats that linear classifiers miss.

Three systems work together:

1. **GNN Detection Engine** — Models the network as a graph; identifies anomalous node/edge patterns indicative of attacks
2. **Self-Healing RL Agent** — Autonomously responds to and resolves detected incidents without human intervention
3. **Decentralized Audit Layer** — Every detection and resolution event is logged to IPFS with Merkle Tree verification — tamper-proof, with no single point of failure

---

## 📊 Performance Highlights

| Metric | Value |
|---|---|
| Detection Accuracy | **99.2%** |
| Response Time | **< 50ms** |
| Incident Resolution (before) | 4.2 hours (manual) |
| Incident Resolution (after RL) | **8.3 seconds** |
| Audit System | Decentralized — IPFS + Merkle Trees |

---

## 🧠 How It Works

### 1. GNN Detection Engine
Network traffic and system events are modeled as a graph — nodes are entities (hosts, services, users), edges are interactions. The GNN learns what a healthy graph looks like and flags deviations in real time. SHAP and LIME are layered on top to explain *why* a particular node or interaction was flagged — making detections auditable, not just accurate.

### 2. Self-Healing RL Agent
When a threat is confirmed, the RL agent takes over. It has been trained across thousands of simulated incident scenarios and has learned to select the optimal remediation action for each threat type. It improves autonomously with every incident it resolves — no redeployment required.

### 3. Decentralized Audit System
Every detection, decision, and resolution is hashed into a Merkle Tree and pinned to IPFS. This means:
- No central server can be compromised to alter logs
- Every entry is independently verifiable
- The audit trail is permanent and append-only

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| **API Framework** | FastAPI (Python) |
| **Detection Model** | Graph Neural Network (GNN) |
| **Explainability** | SHAP, LIME |
| **RL Agent** | Reinforcement Learning |
| **Audit Layer** | IPFS, Merkle Trees |
| **Containerization** | Docker, Docker Compose |

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- Docker & Docker Compose

### Run Locally

```bash
# Clone the repo
git clone https://github.com/DivekManan/desh-ai-backend.git
cd desh-ai-backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Start the API server
uvicorn main:app --reload --port 8000
# API available at http://localhost:8000
# Swagger docs at http://localhost:8000/docs
```

### Run with Docker

```bash
docker build -t desh-backend .
docker run -p 8000:8000 desh-backend
```

### Run the Full System (Backend + Frontend)

```bash
docker-compose up --build
# Backend  → http://localhost:8000
# Frontend → http://localhost:3000
```

---

## 📡 API Reference

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | System health check |
| POST | `/api/detect` | Submit network event for threat detection |
| GET | `/api/incidents` | List all detected incidents |
| POST | `/api/incidents/resolve` | Trigger RL agent to resolve an incident |
| GET | `/api/audit` | Retrieve tamper-proof audit log from IPFS |
| GET | `/api/metrics` | System-wide performance and detection metrics |

### Example — POST `/api/detect`

```json
{
  "source_ip": "192.168.1.45",
  "destination_ip": "10.0.0.1",
  "event_type": "lateral_movement",
  "payload_size": 4096,
  "timestamp": "2025-06-15T10:30:00Z"
}
```

Response includes threat classification, SHAP explanation, confidence score, and recommended action.

---

## 🗂️ Project Structure

```
desh-ai-backend/
├── main.py                    # FastAPI app entry point
├── config.py                  # Environment settings
├── models.py                  # Pydantic schemas
├── requirements.txt
├── routers/
│   ├── health.py
│   ├── detect.py              # POST /api/detect
│   ├── incidents.py           # Incident management
│   ├── audit.py               # IPFS audit log
│   └── metrics.py             # System metrics
├── ml/
│   ├── gnn_detector.py        # Graph Neural Network model
│   ├── shap_explainer.py      # SHAP/LIME explainability
│   ├── rl_agent.py            # Self-healing RL agent
│   └── pipeline.py            # ML orchestrator
├── audit/
│   ├── merkle_tree.py         # Merkle Tree implementation
│   └── ipfs_client.py         # IPFS interaction layer
├── Dockerfile
└── docker-compose.yml
```

---

## 🔗 Related Repository

| Repo | Description |
|---|---|
| [desh-ai-frontend](https://github.com/DivekManan/desh-ai-frontend) | React dashboard — real-time threat feed, audit log viewer, SHAP panels |

---

## 💡 Why Decentralized Audit?

Traditional SIEM systems store logs in a central database. If that database is compromised, so is the entire audit trail. By anchoring every event to IPFS with Merkle Tree verification, DESH-QSI ensures that no single point of failure can erase or alter the incident history — a critical property for security systems that may themselves be under attack.

---

## 👤 Author

**Divek Manan**
Final-year CSE student at Vellore Institute of Technology
📧 divekmanan@gmail.com
🔗 [linkedin.com/in/divek-manan](https://linkedin.com/in/divek-manan)
🐙 [github.com/DivekManan](https://github.com/DivekManan)

---

*If this project was useful or interesting to you, consider giving it a ⭐*