# LEIA Mission Control 🛰️

A production-ready, full-stack 3D orbital visualization platform and autonomous telemetry assistant built for the **Vinterstellar** aerospace initiative. Leia interfaces directly with real-time tracking streams, logs mission coordinates into a relational persistent layer, and leverages an integrated, physics-calibrated Neural Hawkes Surrogate Network for space situational awareness.

---
## 🖥️ Mission Interface Preview

| Global Telemetry View | Data-Aware AI Agent Console & Telemetry | Data-Aware AI Agent Console |
| --- | --- | --- |
| ![3D Orbital Canvas](./assets/telemetry-view.png) | ![Leia RAG Terminal](./assets/Leia_prompt_trajectory.png) | ![Leia RAG Terminal](./assets/leia-console-view.png) |

---

## 🛠️ System Architecture & Data Loop

The ecosystem relies on containerized operational layers built for high-throughput streaming and live inference:

1. **The Core Web Dashboard (Frontend):** React + Vite executing a declarative 3D viewport canvas powered by Three.js (`@react-three/fiber`). It handles real-time visual synchronization and seamless z-index console overlay layering for enhanced dashboard interaction.
2. **The Asynchronous Telemetry Server (Backend):** FastAPI managing asynchronous multi-service IO operations, serving high-frequency mathematical endpoints, and routing predictive telemetry states.
3. **The Intelligent Agent Subsystem (AI & Data):** An optimized execution pipeline that queries a highly available PostgreSQL instance via SQLAlchemy, constructs context-aware prompt matrices from live catalog snapshots, and handles agent reasoning utilizing the official `google-genai` SDK.
4. **The Physics Surrogate Engine (AI Inference):** A localized, physics-regularized **Neural Hawkes Surrogate Network** (`PyTorch`) that replaces standard linear kinematics with real-time, non-linear spatiotemporal cascade intensity maps.

---

## 🚀 Core Features

- **Real-Time Telemetry Synchronization:** Asynchronous pooling hooks stream active positional metrics from the International Space Station (ISS).
- **Dynamic 3D Orthogonal Mapping:** Interactive WebGL viewport displaying satellite orbits, dynamic atmosphere scaling, and telemetry path retention.
- **Relational Session Ledger:** One-click coordinate snapshot logging into a production-managed managed PostgreSQL database instance.
- **Space Situational Awareness (SSA) Simulation Engine:** On-demand generation of synthetic orbital cascade scenarios executing dynamic secondary collision tracking and non-linear decay curves.
- **Physics-Informed AI Weights Inference:** Pre-trained and calibrated neural network hidden layers configured to calculate sub-50ms spatiotemporal intensity vectors without falling back to static numerical safe-modes.
- **Context-Aware AI Co-Pilot (RAG):** An integrated Gemini agent synced directly with the active database layout to calculate data properties, parse tracking parameters, and explain real-time simulation runs.

---

## 📐 The Mathematical & Neural Framework

The core engine transforms Earth-Centered, Earth-Fixed (ECEF) global coordinates into a Three.js coordinate grid ($X, Y, Z$) around a normalized sphere where $R_{Earth} = 1$:

$$Radius = 1 + \left(\frac{Altitude}{6371}\right)$$
$$X = -Radius \cdot \cos(\theta) \cdot \cos(\phi)$$
$$Y = Radius \cdot \sin(\theta)$$
$$Z = Radius \cdot \cos(\theta) \cdot \sin(\phi)$$

*Where $\theta$ represents the Geodetic Latitude radian value, and $\phi$ represents the Geodetic Longitude radian value.*

For advanced cascade forecasting, the system drops classic linear assumptions and queries a physics-regularized deep neural layout optimizing structural loss combined with a physical constraints boundary ($\text{ReLU}$ violation clipping):

$$\mathcal{L}_{\text{total}} = \mathcal{L}_{\text{MSE}} + 10.0 \cdot \mathbb{E}\left[\max(0, -\hat{y}_{\text{drag}})\right]$$

---

## 🛰️ Production Deployment Metrics
Backend Host: Deployed via Docker Container runtimes to cloud platforms.
Frontend Core: Static optimization tree bundles delivered through Global Content Delivery Networks (CDNs).
Database Stack: Production-grade managed cloud PostgreSQL database cluster.

---
## 📦 Local Setup & Deployment

### Backend Infrastructure (FastAPI)
Navigate to the root directory and establish a localized virtual environment:

``` Bash
cd leia-mission-control
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
