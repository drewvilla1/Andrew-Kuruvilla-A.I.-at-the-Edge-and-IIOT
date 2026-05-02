# Andrew Kuruvilla — ITAI 3377 Course Portfolio

**Course:** A.I. at the Edge & IIOT(ITAI 3377)  
**Institution:** Houston City College

---

## About Me

Hi, I'm Andrew Kuruvilla. I'm STUDYING A.I. and Robotics at Hcc, and I took this course to learn how edge computing and IoT can bring intelligent,
real-time decision-making to manufacturing, smart cities, and networked devices. This
course gave me hands-on exposure to the full stack of Industrial AI: from protocol-level
sensor communication to machine learning model development and autonomous agent design.

---

## Labs

### Lab 02 — Development Environment Exploration
**What I did:** Engaged with the material conceptually, analyzing the tools and frameworks
used for Edge AI and IoT development, including their trade-offs and use cases.  
**What I learned:** How to evaluate the purpose and fit of different development environments
for constrained, real-time AI systems.  
**Challenge I faced:** Deciding between a conceptual vs. hands-on approach and structuring
my analysis clearly.

---

### Lab 03 — Edge AI Model Deployment (MNIST on Edge Impulse)
**What I did:** Trained a Convolutional Neural Network (CNN) on the MNIST handwritten
digit dataset, converted it to TensorFlow Lite, and deployed it to a simulated edge device
using Edge Impulse's Bring Your Own Model (BYOM) feature via WebAssembly in-browser.  
**What I learned:** How edge optimization works in practice — TFLite strips away overhead
to enable fast, local inference (1–5 ms per image) with a tiny memory footprint (~70–300 KB
RAM). I also saw how this mirrors real deployments like the Liverpool Smart Pedestrians
project, where privacy and low latency are critical.  
**Challenge I faced:** Initial confusion with the Edge Impulse upload process — switching to
the BYOM web interface resolved it. I also observed that int8 quantization caused a small
accuracy drop (~0.5–1%), a real trade-off between speed and precision on edge hardware.

---

### Lab 04 — IIoT Sensor Network Simulation (MQTT, CoAP, OPC UA)
**What I did:** As part of a four-person team, I led the CoAP and OPC UA implementations —
building an observable CoAP server resource and an OPC UA server with a writable
address space, then testing client interactions with both.  
**What I learned:** No single protocol fits all IIoT scenarios. MQTT excels in scalability and
simplicity, CoAP is ideal for constrained low-power devices, and OPC UA provides the
rich information modeling and security needed for serious industrial automation.
I also deepened my understanding of asynchronous Python and managing event loops
across operating systems.  
**Challenge I faced:** CoAP and OPC UA scripts had asyncio event loop errors on Windows
and endpoint mismatches that required careful debugging with tools like UaExpert.

---

### Lab 06 — IIoT Temperature Time Series Forecasting with VAE Data Augmentation
**What I did:** Applied time-series forecasting to a 97,000+ row Kaggle IoT temperature
dataset. I preprocessed the data (datetime conversion, chronological sorting, lag features
`temp_lag_1`/`temp_lag_2`, rolling mean), trained a SeasonalNaive forecasting model
(seasonal length = 24), ran rolling-origin cross-validation across 5 windows, then built
and trained a Variational Autoencoder (VAE) to generate synthetic data and retrained
the model on the augmented dataset.  
**What I learned:** The SeasonalNaive model achieved MAE = 4.65 and RMSE = 5.73 as a
baseline, with cross-validation confirming consistent performance (CV MAE = 0.405).
The VAE augmentation actually degraded results (augmented MAE = 5.22, RMSE = 6.18),
which taught me that data quality matters far more than data quantity — poorly generated
synthetic data actively hurts model performance. Future improvements would use LSTM,
Transformer architectures, or GAN-based generators for more realistic augmentation.  
**Challenge I faced:** Understanding why the augmented model performed worse, and
connecting the VAE's reconstruction loss and KL divergence to the quality of the synthetic
sequences it produced.

---

### Lab 07 — Age of Information & ML in IIoT Networks
**What I did:** Worked with a 10,000-row IIoT network dataset to explore Age of Information
(AoI) and reliability. I cleaned the data (removing 1,397 invalid rows), built four
visualizations (scatter, box plots, correlation heatmap, AoI-PLP trade-off), and trained a
Random Forest Regressor to predict AoI from network features.  
**What I learned:** The model achieved R² = 0.997 and RMSE = 6.85, showing that
packet_loss_probability (feature importance: 0.77) and transmission_probability (0.23)
are the dominant predictors of information staleness. Channel quality is the key leverage
point for network optimization.  
**Challenge I faced:** Connecting the model's feature importance scores back to what they
mean for real IIoT network design decisions — bridging the math and the application.

---

## Assignments

### Assignment 01 — Edge AI & IoT Development Tools
**Problem:** Develop a conceptual understanding of the key development environments and
tools used for Edge AI and IoT projects.  
**Approach:** Researched and analyzed the purpose, functionality, and typical use cases of
tools such as Edge Impulse, TensorFlow Lite, and IoT communication frameworks.  
**Results:** A structured overview connecting each tool to its industrial application and
explaining when and why each would be chosen.  
**Reflection:** This assignment set the foundation for the whole course — understanding why
these tools exist made every subsequent lab much easier to navigate with context.

---

### Assignment 03 — Case Study: Liverpool Smart Pedestrians Project
**Problem:** Critically analyze the edge-computing video analytics system deployed in
Liverpool, NSW for real-time traffic monitoring.  
**Approach:** Evaluated the system's methodology (NVIDIA Jetson TX2 + YOLOv3 + SORT),
performance (69% mean accuracy, ~20 fps), privacy-by-design architecture, and results
from two real-world field trials.  
**Results:** The system monitored 631 pedestrians in an indoor trial and revealed daily and
weekly mobility patterns across Liverpool's CBD over a week-long outdoor deployment.
That data fed directly into the city's updated mobility plan.  
**Reflection:** Retrofitting existing CCTV with edge processing solved privacy, cost, and
latency problems simultaneously. I also recognized that today's hardware (Jetson Orin,
YOLOv8, ByteTrack) would significantly improve on the 2019 results — a good reminder
that evaluating technology means evaluating it in its time.

---

### Assignment 04 — Reflective Journal: IIoT Sensor Network (Lab 04)
**Problem:** Reflect personally on the Lab 04 IIoT protocol simulation project.  
**Approach:** Documented my specific contributions (CoAP + OPC UA), learning outcomes
per protocol, team challenges, and connections to real Industry 4.0 deployment scenarios.  
**Results:** A detailed personal reflection linking protocol trade-offs to industrial decisions —
for example, combining MQTT for cloud telemetry with OPC UA for on-premise machine
control in hybrid architectures.  
**Reflection:** Technical debugging (asyncio loops, port conflicts, library versions) is just as
important a skill as understanding the protocols themselves — you can't deploy what you
can't troubleshoot.

---

### Assignment 06 — Presentation: IIoT Time Series Forecasting Findings & Recommendations
**Problem:** Summarize the findings and recommendations from Lab 06's time-series
forecasting project in a presentation format for a technical audience.  
**Approach:** Built a 10-slide presentation covering the full pipeline — dataset overview
(97K+ records), preprocessing steps, SeasonalNaive model selection and rationale,
performance metrics, cross-validation strategy, VAE architecture and purpose, augmented
results, and key insights.  
**Results:** Clearly communicated that the SeasonalNaive baseline (MAE = 4.65, RMSE = 5.73)
outperformed the VAE-augmented model (MAE = 5.22, RMSE = 6.18 — a 12% increase in
error), with the root cause identified as the synthetic sequences failing to capture true
temperature dynamics.  
**Reflection:** Translating technical results into a clear presentation forced me to articulate
*why* something failed, not just *that* it failed. The recommendation to explore LSTMs,
Transformers, and GAN-based generators came directly from understanding the VAE's
specific weaknesses in this context.

---

### Midterm — Cybersecurity Plan for an AI-Integrated IIoT System
**Problem:** Design, implement, and assess a comprehensive cybersecurity plan for a
hypothetical AI-integrated IIoT system.  
**Approach:** Developed a security architecture addressing threats across the sensor, edge,
and cloud layers, incorporating authentication, encryption, anomaly detection, and
incident response planning. Applied protocol-specific security (TLS for MQTT, DTLS for
CoAP, certificates for OPC UA).  
**Results:** A full cybersecurity plan covering threat modeling, layered defenses, and
AI-driven anomaly detection tailored to an IIoT environment.  
**Reflection:** Designing security from the ground up made clear how often it is an afterthought
in IoT deployments — and how much harder it is to retrofit than to build in from the start.

---

### Assignment 09 — Case Study: Autonomous Agents in Industry 4.0 (AGVs with DDQN)
**Problem:** Analyze Hjulström's (2022) research on reinforcement learning for Automated
Guided Vehicles (AGVs) in an Industry 4.0 simulation.  
**Approach:** Examined the Multi-Agent System design (3 agents on a 10×10 grid, DDQN
algorithm), reward structure (+100 task, –70 collision, –100 battery failure), curriculum
training over 200,000 episodes, and final performance metrics.  
**Results:** In testing, agents completed all 300 tasks with zero collisions and zero battery
failures, averaging only 2.59 extra steps beyond the optimal route. Analyzed limitations
(clean simulation, fixed layout, no inter-agent communication) and future directions.  
**Reflection:** The reward design section stood out — small changes to reward signals produce
dramatically different learned behaviors. It also changed how I think about "autonomous":
agents with only local observations can develop surprisingly coordinated behavior without
ever communicating directly with each other.

---

### Capstone Project — AI-Driven Autonomous Agent in an IIoT Environment
**Problem:** Design, develop, and deploy an AI-driven autonomous agent using generative AI
within an IIoT environment, integrating edge computing for real-time decision-making,
autonomous operations, and security.  
**Approach:** [Add your brief description of tools, architecture, and approach here]  
**Results:** [Add a summary of what your agent accomplished]  
**Reflection:** [Add your key takeaway from the capstone]

---

## Key Skills Developed

Through this course I built practical experience in: IIoT protocol implementation (MQTT,
CoAP, OPC UA), edge AI deployment (TensorFlow Lite, Edge Impulse), machine learning
for network analytics (Random Forest, feature engineering, pandas), reinforcement learning
concepts (DDQN, reward design, multi-agent systems), cybersecurity planning for industrial
AI systems, and asynchronous Python programming.

---

*Course: ITAI 3377 — A.I. at the Edge & IIOT/ Spring 2026

