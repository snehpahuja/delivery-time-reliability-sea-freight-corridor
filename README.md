# Shanghai-New York Container Shipping Reliability: Monte Carlo Simulation

A Monte Carlo simulation analyzing delivery time reliability on the Shanghai-New York shipping corridor, developed as a capstone project for Advanced Optimization and Simulation (BUAN402) at FLAME University.

## Overview

This project quantifies the gap between carrier-quoted delivery schedules (38 days) and actual operational reality through probabilistic modeling of six sequential journey legs, incorporating real-world risks like weather, port congestion, and infrastructure bottlenecks.

## Key Findings

| Metric | Value |
|--------|-------|
| **Mean Cargo Lead Time** | 46.78 days (vs. 38-day quote) |
| **On-Time Probability (≤38 days)** | 45.98% |
| **Severe Delay Risk (≥45 days)** | 28.11% |
| **95th Percentile Lead Time** | 47.02 days |
| **Port Dwell Component** | 5.91 days |

**Key Insight:** Nearly 1 in 3 containers experience delays >45 days due to cascade failures at Cartagena transshipment hub.

## Methodology

- **Model Type:** Monte Carlo simulation with triangular distributions
- **Sample Size:** 5,000 journeys × 150 runs (fully converged)
- **Route Components:** 6 legs (Shanghai port → Pacific crossing → Panama Canal → Cartagena transshipment → Atlantic crossing → New York port)
- **Risk Model:** Dual-scenario distributions to capture binary operational states (normal vs. disruption)

## Files

- `DeliveryTimeReliabilityReport.pdf` — Full research report with analysis and recommendations
- `DeliveryTimeReliabilityModel.xlsx` — Executable Monte Carlo model with convergence testing

## How to Use

1. Open `DeliveryTimeReliabilityModel.xlsx` in Excel
2. Navigate to the "Inputs & Assumptions" sheet to adjust parameters
3. View pre-calculated results in "Outputs & Analysis" sheet
4. Convergence testing visible across journey count scales (100–5,000)

**Parameters you can modify:**
- Steaming speed probabilities
- Panama Canal drought likelihood
- Port dwell times
- Carrier quote baseline (default: 38 days)

## Business Applications

 **For Shippers:**
- Use 95th percentile (47.02 days) instead of quoted (38 days) for supply chain planning
- Implement tiered alert protocols (Day 40 yellow alert, Day 45 red alert)
- Negotiate percentile-based SLAs with carriers

 **For Carriers:**
- Identify reliability as competitive differentiator
- Benchmark against industry standards (Beacon: 13.9% on-time for 2025)

## Technical Details

**Model Design:**
- Triangular distribution formula: Inverse CDF sampling with min/mode/max parameters
- Independence assumption: Leg risks modeled independently; cumulative time additive
- Cascade logic: 7-day penalty if Pacific delays cause missed Cartagena connection

**Validation:**
- Convergence testing: SD dropped 85% (0.842 → 0.127 days) from 100 to 5,000 journeys
- Consistency check: Model findings align with Beacon Maritime 2025 data (47.4% very late)

## Future Research

- Route comparison: Suez Canal vs. Cape of Good Hope alternatives
- Conditional probability modeling: Upstream delays → downstream risk escalation
- Real-time Bayesian updating: Live monitoring system using vessel tracking data
- Sensitivity analysis: Which parameters (drought %, labor disruption %) drive highest impact

## About

**Author:** Sneh Pahuja (220357)  
**Course:** Advanced Optimization and Simulation (BUAN402)  
**Institution:** FLAME University  
**Date:** April 2026

---

**Want to discuss this project?** Feel free to open an issue or contact me.
