# Legacy Asset Reliability: AI-Driven Predictive Maintenance Retrofit

Project Overview
This project demonstrates how to transition a manufacturing facility from Preventative (Fixed-Interval) maintenance to Predictive (Condition-Based) maintenance. By utilizing a synthetic dataset of 10,000 industrial sensor readings, I developed a machine learning model designed to reduce unplanned downtime—a primary driver of lost throughput in US manufacturing.

The Business Case
  Problem: Fixed-interval maintenance (e.g., every 200 mins of tool wear) is inefficient. It leads to either "over-maintaining" (wasting tool life) or "under-maintaining" (risking 4+ hours of emergency downtime).
  Goal: Create a "Traffic Light" early warning system with at least 24 hours of lead time for the maintenance team.
  Target KPIs: Overall Equipment Effectiveness (OEE), Mean Time To Repair (MTTR), and Scrap Rate.

Key Technical Actions
1. Physics-Based Feature Engineering
Rather than relying on raw data alone, I applied Industrial Engineering principles to create an Interaction Feature called Stress_Factor.
Formula: StressFactor=ToolWear×Torque
Rationale: A dull tool combined with high force accelerates failure exponentially. This feature became the top predictor in the model's feature importance.

2. Machine Learning Pipeline
Model: Random Forest Classifier (chosen for high interpretability and feature importance analysis).
Evaluation: Focused on Recall over Accuracy to ensure the "safety net" was wide enough to catch critical failures.

Results & Strategic Tuning
I tuned the model using a custom probability threshold of 0.3 to prioritize factory uptime:

Baseline (0.5 threshold)
Metrics:
Recall (Catch Rate) = 69%
Precision	= 93%

Optimized (0.3 threshold)
Metrics:
Recall (Catch Rate) = 77%
Precision = 77%

By accepting a slightly lower Precision (more "checks"), the model significantly reduces the risk of a catastrophic "False Negative" failure, potentially saving thousands in emergency repair costs.
