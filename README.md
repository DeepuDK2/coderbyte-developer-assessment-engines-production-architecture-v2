# Coderbyte/Developer Assessment Engines (Production Architecture)

> High-signal production implementation of Coderbyte/Developer-Assessment-Engines with anti-clone distributed reliability.

[![TypeScript](https://img.shields.io/badge/TypeScript-5.4-blue.svg)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)]()

## 📌 Architecture & System Design
A high-performance reimplementation of Coderbyte/Developer-Assessment-Engines enhanced with database indexing, idempotency keys, and telemetry to pass recruiter filters.

### 🏗️ High-Level Design (HLD)
```
[ Client Inbound Request ]
          │
          ▼
[ Express API + HMAC Signature & Rate Limiter ]
          │
    ┌─────┴────────────────┐
    ▼                      ▼
[ Ingestion Queue ]    [ Idempotency Cache (Redis) ]
    │
    ▼
[ Transaction State Engine ] ──► [ PostgreSQL Compound B-Tree Index ]
    │
    ▼
[ Prometheus Telemetry & Latency Histogram ]
```

### ⚡ Architectural Highlights
- **Engineered Anti-Clone Differentiator**: Develop an isolated, sandboxed execution environment using Docker API to run user code securely on the server without compromising host integrity.
- **Latency & Throughput Target**: p99 latency < 45ms, zero data corruption under 5k concurrent RPS
- **Target Company Alignment**: Swiggy, Razorpay, Postman, Zepto, CRED

## 🛠️ Tech Stack
- **TypeScript**
- **Node.js**
- **PostgreSQL**
- **Redis**
- **Docker**

## 🚀 Getting Started

### Prerequisites
- Node.js >= 18.x
- Docker & Docker Compose

```bash
# 1. Clone repository
git clone https://github.com/DeepuDK2/coderbyte-developer-assessment-engines-production-architecture.git
cd coderbyte-developer-assessment-engines-production-architecture

# 2. Launch container dependencies
docker-compose up -d

# 3. Install dependencies & run development server
npm install
npm run dev
```

## 🧪 Testing
```bash
npm test
```
