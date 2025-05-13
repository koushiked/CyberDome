# IoT IDS App

A Cloud-Based AI Intrusion Detection System for IoT Networks

---

## 🚀 About This Project

Welcome to the **IoT IDS App**—an AI-powered cloud-based **Intrusion Detection System (IDS)** designed specifically for **IoT networks**. This system helps detect and classify various cyber attacks using an **Extreme Gradient Boosting (XGBoost) model**, ensuring security and peace of mind for IoT environments.

## 📂 Project Structure
Here's a quick breakdown of how the project is organized:

```
├── LICENSE              # License details
├── README.md           # You are here!
│
├── main.py             # Runs data transformation and model training
├── app.py              # Starts the API service
├── streamlit_app.py    # Runs the web app interface
│
├── data/               # Contains all datasets
│   ├── external        # Third-party data sources
│   ├── processed       # Final, cleaned data for training
│
├── models/             # Saved trained models
├── notebooks/          # Jupyter notebooks for experimentation
├── reports/            # Analysis reports
│
├── src/                # Core project files
│   ├── data/           # Data processing scripts
│   ├── features/       # Feature engineering scripts
│   ├── models/         # Model training and prediction scripts
│   ├── utils/          # Utility scripts for logging and configuration
│
└── requirements.txt    # Dependencies and package requirements
```

---

## 📊 Dataset Overview
This system detects different types of attacks found in IoT networks, including:

- **MITM (Man-in-the-Middle) ARP Spoofing**
- **DoS (Denial-of-Service) SYN Flooding**
- **Host and Port Scanning**
- **Mirai Malware Attacks (UDP, ACK, HTTP Flooding, Host Bruteforce)**

The dataset is sourced from the **CSE-CIC-IDS2018 dataset**, containing both benign and malicious network traffic.

---

## 🏗 System Architecture

### 🔧 Training Pipeline
1. **Data Ingestion** → Packet data is loaded into dataframes.
2. **Preprocessing** → Data is cleaned and prepared.
3. **Model Training** → The XGBoost model is trained, evaluated, and saved if it performs well.

### 🔍 Inference Pipeline
- The **API module** loads the trained model and provides endpoints for predictions.
- Users can upload network traffic data and receive **real-time analysis** of possible intrusions.

### 📡 Real-time Monitoring
- This system can **stream live network traffic** to detect intrusions in real time.
- If real-time data isn’t available, we simulate streaming using pre-recorded datasets.

### 🌐 Deployment Setup
- The **API engine** is hosted on **AWS EC2**.
- The **User Interface (UI)** connects to the API via **HTTPS**, showing real-time attack classifications.

---

## 📈 Performance Metrics
Our **XGBoost model** delivers top-tier accuracy:

- **F1 Macro Average**: 0.997
- **F1 Weighted Average**: 1.0
- **Inference Time per Data Point**: **~10 microseconds** ⚡
- **Training Time**: **~151 seconds** 🚀

---

## 🛠 Getting Started
Want to try the **IoT IDS App**? Check it out here: **[IOT IDS App](https://iotids.streamlit.app/)** *(Note: The server may not always be up since the app is still in beta!)*

### 🚀 How to Use
1. Upload a **PCAP** or **PCAPNG** file (network packet data).
2. Click **"Process"** to start data processing.
3. Click **"Activate IDS"** to analyze packets.
4. Click **"Download Analysis File"** to get a CSV of flagged packets.

---

## 🔬 Experimenting with the Model
### 🖥 Requirements
- **Windows 10 / Ubuntu** (or any suitable OS)
- **Python 3.10+**
- **Wireshark/tshark** (for packet analysis)

### 🏗 Running Locally
1. **Clone the repo**:
   ```bash
   git clone https://github.com/Myth20049/Cyber_Dome.git
   ```
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Download the dataset** [here](https://ieee-dataport.org/open-access/iot-network-intrusion-dataset) and move it to `data/external/`, then unzip it.
4. **Train the model** (⚠️ This takes a while!):
   ```bash
   python main.py
   ```
5. **Start the API**:
   ```bash
   python app.py
   ```
6. **Run the web app**:
   ```bash
   streamlit run streamlit_app.py
   ```

---

## 🚀 Deploying the App
### ☁️ API Server Setup (AWS EC2)
1. **Create an AWS EC2 (Ubuntu) instance.**
2. **Update your instance:**
   ```bash
   sudo apt-get update
   ```
3. **Install dependencies:**
   ```bash
   sudo apt install python3-pip
   pip3 install -r requirements.txt --no-cache-dir
   ```
4. **Run the API to test:**
   ```bash
   python3 app.py
   ```
5. **Configure Nginx** (Follow [this guide](https://lcalcagni.medium.com/deploy-your-fastapi-to-aws-ec2-using-nginx-aa8aa0d85ec7) under *Nginx configuration*).
6. **Install tshark**:
   ```bash
   sudo apt install tshark
   ```

### 🌍 Deploying the Web App
1. **Create an account on** [streamlit.io](https://streamlit.io).
2. **Create a Streamlit app** using your GitHub repo.
3. **Set `streamlit_app.py` as the main script**.
4. **Set Python version to `3.10`** before launching.

🎉 *Congrats!* You’ve successfully deployed the **IoT IDS App**! 🚀

🚀 **Stay secure, stay ahead!** 🔐

