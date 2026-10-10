# CreditLens — AI-Powered Credit Risk Intelligence Platform

[![Live Demo](https://img.shields.io/badge/Live-Demo-creditlens--credit--risk.onrender.com-blue?style=flat-square)](https://creditlens-credit-risk.onrender.com)
[![Test Suite](https://img.shields.io/badge/pytest-44%20passed-emerald?style=flat-square&logo=pytest)](tests)
[![Python](https://img.shields.io/badge/python-3.11%20%7C%203.14-blue?style=flat-square&logo=python)](requirements.txt)
[![Dual ML](https://img.shields.io/badge/ML-EBM%20(GA²M)%20%2B%20LightGBM-cyan?style=flat-square)](src/xai/)
[![Inference Engine](https://img.shields.io/badge/Inference-Live%20%7C%20Offline-purple?style=flat-square)](src/talk_to_data/router.py)
[![Container](https://img.shields.io/badge/Docker-Multi--Stage%20Hardened-2496ED?style=flat-square&logo=docker)](Dockerfile)

---

## 1. Executive Summary

In consumer banking and commercial underwriting, machine learning platforms face a fundamental regulatory dilemma: **predictive accuracy versus explainability**. High-capacity gradient boosting models achieve superior risk discrimination, but their black-box nature creates strict compliance barriers under the **Fair Credit Reporting Act (FCRA, 15 U.S.C. § 1681m)** and **Equal Credit Opportunity Act (ECOA, 12 C.F.R. § 1002.9 - Regulation B)**.

**CreditLens** solves this by unifying:
1. **Dual Machine Learning Underwriting**: A Glassbox **Explainable Boosting Machine (EBM / $GA^2M$)** providing mathematically exact additive scorecards side-by-side with an isotonically calibrated **LightGBM** model.
2. **Automated Regulatory Adverse Action Engine**: Translates algorithmic log-odds and TreeSHAP negative attributions directly into compliant **FCRA / ECOA Form C-1** denial notices.
3. **ML-Derived Credit Underwriting Rules**: Transparent If-Then policy rules extracted from surrogate decision trees with empirical Support, Confidence, and Risk Lift metrics.
4. **Autonomous Talk-to-Data Assistant**: Natural language to SQL query engine backed by an in-process **DuckDB** analytical warehouse, protected by an **AST security guardrail**, **token-bucket rate limiter**, **UI debouncer**, and a **4-tier LLM fallback cascade**.
5. **Progressive Disclosure UI**: An institutional, zero-emoji banking terminal built for underwriters and credit committees, presenting actionable signals first and technical telemetry on demand.

### Live Demo

The platform is deployed and running at: **[https://creditlens-credit-risk.onrender.com](https://creditlens-credit-risk.onrender.com)**

*(Note: If no API key is provided, the platform automatically activates the deterministic fallback tier, guaranteeing all benchmark inquiries run flawlessly with 0 network dependencies.)*

---

### Quick Start (Under 60 Seconds)

#### Option A: Single-Command Docker Deployment (Recommended)

```zsh
# 1. Clone repository
git clone https://github.com/K1NGS1LVER/creditlens.git
cd creditlens

# 2. (Optional) Provide LLM API key for live inference
cp .env.example .env
# Edit .env to add your API key if desired

# 3. Launch the containerized platform
docker compose up --build
```

Access the application at: **`http://localhost:8501`**

#### Option B: Local Python Development
```zsh
# 1. Activate your virtual environment (Python 3.11+)
source .venv/bin/activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run full automated test suite
pytest tests/ -v

# 4. Launch Streamlit interface
streamlit run app.py
```

---

## 2. End-to-End System Architecture