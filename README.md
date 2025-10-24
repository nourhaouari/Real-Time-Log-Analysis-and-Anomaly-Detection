# Real-Time Log Analysis and Anomaly Detection
Streaming and Batch Data Engineering with Kafka, Spark &amp; HDFS


## Real-Time Log Analysis and Anomaly Detection

This repository presents a complete implementation of a real-time log processing and anomaly detection pipeline. 
It integrates Apache Kafka for data streaming, Apache Spark for both streaming and batch analytics, and HDFS for distributed data storage. 
Additionally, a PyWebIO dashboard is provided for interactive monitoring of system metrics and performance indicators.

---

## 1. Overview

The system is designed to simulate, collect, and analyze web server logs in real time. 
It produces synthetic log data, streams it via Kafka, and processes it with Spark to identify anomalies, 
generate statistics, and output summarized insights in structured JSON format.

This pipeline demonstrates an end-to-end data engineering workflow, from ingestion to visualization.

---

## 2. Architecture

### Components

- Kafka Producer: Generates and streams simulated log data.
- Apache Kafka Broker: Buffers and manages message delivery to consumers.
- Spark Consumer: Processes Kafka streams in real time, applying transformations and anomaly detection.
- HDFS / Local Storage: Persists summaries and structured analytics data.
- Dashboard (PyWebIO): Displays real-time aggregated insights through a web interface.

### Data Flow

```
Log Generator → Kafka Topic → Spark Structured Streaming → summary.json → PyWebIO Dashboard
```

---

## 3. Project Structure

```
project/
│
├── analysis/
│   └── realtime_dashboard.py        # PyWebIO dashboard
│
├── config/
│   ├── kafka_settings.py            # Kafka topic and server configuration
│   └── spark_config.py              # Spark session setup and schema definitions
│
├── producers/
│   ├── auto_producer.py             # Kafka producer for continuous logs
│   ├── log_generator.py             # Log generator using Faker
│   └── log_producer.py              # Alternative producer script
│
├── consumers/
│   └── spark_consumer.py            # Spark streaming consumer
│
├── results/
│   ├── summary.json                 # Aggregated analytics results
│   └── testspark.py                 # Test consumer
│
└── README.md                        # Project documentation
```

---

## 4. Technologies Used

| Component | Technology |
|------------|-------------|
| Messaging Layer | Apache Kafka |
| Stream Processing | Apache Spark Structured Streaming |
| Storage | HDFS / Local JSON |
| Data Simulation | Python Faker |
| Visualization | PyWebIO |
| Runtime Environment | Java 8, Hadoop winutils, Python 3.10+ |

---

## 5. Installation and Setup

### Step 1: Prerequisites

- Java 8 (e.g., D:\java\jdk8)
- Hadoop (winutils) (e.g., D:\hadoop-3.3.5)
- Running local Kafka and Zookeeper services
- Python dependencies:

```bash
pip install kafka-python pyspark pywebio faker
```

### Step 2: Start Kafka and Zookeeper

```bash
zookeeper-server-start.bat config/zookeeper.properties
kafka-server-start.bat config/server.properties
```

### Step 3: Start the Producer

```bash
python producers/auto_producer.py
```

### Step 4: Run the Spark Consumer

```bash
python consumers/spark_consumer.py
```

### Step 5: Launch the Dashboard

```bash
python analysis/realtime_dashboard.py
```
Access at http://localhost:8080

---

## 6. Output Examples

### Kafka Message Example

```json
{
  "timestamp": 1730009852,
  "ip": "192.168.1.22",
  "method": "GET",
  "url": "/products",
  "status": 200
}
```

### summary.json Example

```json
{
  "top_ips": [{"ip": "192.168.1.22", "count": 24}],
  "top_urls": [{"url": "/login", "count": 12}],
  "errors": [{"status": 500, "ip": "192.168.1.5", "url": "/products"}]
}
```



## 7. Author

Nour Haouari  
Biomedical Engineering Student, ISTMT Tunisia    
Email: nourhaouari3@gmail.com  

---



