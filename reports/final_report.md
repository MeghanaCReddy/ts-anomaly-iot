Time Series Anomaly Detection for IoT Sensors
1. Problem Understanding and Approach

The client operates a manufacturing facility with IoT sensors monitoring critical equipment. Unusual sensor readings can indicate equipment failure or maintenance needs. The goal is to detect anomalies in multivariate time series sensor data to enable proactive maintenance.

Approach:

Data Exploration & Cleaning: Load raw sensor data, check missing values, remove invalid readings, and handle outliers.

Feature Engineering: Generate meaningful features (rolling statistics, RMS, kurtosis, energy, trend indicators) to capture sensor signal characteristics.

Anomaly Detection Models:

Isolation Forest (Statistical/Unsupervised): Detects points that are isolated from normal patterns.

Autoencoder (Deep Learning): Learns a compressed representation of normal behavior; large reconstruction errors indicate anomalies.

Evaluation & Visualization: Compare anomaly detection results across methods and visualize detected anomalies per channel.

2. Feature Engineering Rationale

Raw sensor readings alone may not capture subtle anomalies. The following features were engineered:

Feature	Description	Purpose
Rolling Mean	Mean over a sliding window	Detect local trend shifts
Rolling Std	Standard deviation	Identify sudden volatility
Kurtosis	Measure of signal peakiness	Detect extreme spikes
RMS	Root Mean Square	Capture signal magnitude variations
Energy	Sum of squares	Measure overall signal strength

Scaling: Features were standardized to ensure uniform contribution to anomaly detection algorithms.

3. Model Selection and Comparison

Approach 1 — Isolation Forest:

Works by isolating anomalies in a feature space using random splits.

Hyperparameters:

n_estimators=100, max_samples='auto', contamination=0.02 (2% anomalies)

Pros: Fast, interpretable, suitable for high-dimensional data.

Cons: May miss subtle anomalies in correlated features.

Approach 2 — Autoencoder:

Neural network learns normal patterns; anomalies have high reconstruction error.

Architecture:

Input → Encoder (64→32→16) → Bottleneck → Decoder (16→32→64) → Output

Training: Mean squared error loss, 20 epochs, batch size=128.

Pros: Captures nonlinear relationships, works well on complex signals.

Cons: Requires more computation; threshold selection can be tricky.

Comparison:

Isolation Forest detected ~200,700 anomalies; Autoencoder detected ~4,000 anomalies.

Overlap: About 50% of Autoencoder anomalies were also flagged by Isolation Forest.

Visual inspection confirmed anomalies corresponded to unusual sensor spikes.

4. Key Findings and Business Insights

Many anomalies correspond to high vibration or sudden sensor fluctuations, which may indicate potential equipment failure.

Autoencoder captured subtle anomalies that Isolation Forest missed, highlighting the value of deep learning models for complex patterns.

Combined use provides a robust detection framework: statistical methods detect obvious anomalies, while Autoencoder detects hidden anomalies.

Business Impact:

Early detection reduces unplanned downtime.

Allows targeted maintenance instead of reactive repairs.

Supports predictive maintenance strategies in manufacturing facilities.

5. Limitations and Future Improvements

Limitations:

No labeled anomalies for supervised evaluation. Metrics like precision/recall are approximated.

Isolation Forest may not capture temporal correlations.

Autoencoder requires careful threshold tuning for anomaly detection.

Future Improvements:

Implement LSTM Autoencoder to capture temporal dependencies.

Incorporate domain knowledge for labeling historical anomalies.

Use ensemble methods combining multiple detection algorithms for improved reliability.

Deploy real-time streaming anomaly detection for live sensor monitoring.