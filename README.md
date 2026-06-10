# Event-Driven Data Pipeline

Real-time data platform built around Kafka, AWS Lambda, Kubernetes consumers, Airflow, and Snowflake. The repo models an event-driven architecture where streaming ingestion, near-real-time processing, and scheduled analytics workflows all coexist in the same system.

![Architecture Diagram](docs/architecture.png)

## Why this repo matters

This project is a strong architecture portfolio piece because it crosses multiple domains at once: streaming, serverless processing, Kubernetes-based consumers, batch orchestration, and analytics warehousing.

## What is included

- Kafka/MSK infrastructure and supporting Terraform
- Python event producers
- Kubernetes consumer workloads
- Lambda-style event transformation layer
- Airflow DAGs for downstream batch ETL
- Snowflake-oriented analytics pipeline
- monitoring configuration for throughput and consumer lag

## Data flow

1. Producers emit application events into Kafka.
2. Streaming consumers process events from Kubernetes.
3. Lambda/EventBridge components handle transformation and routing tasks.
4. Airflow runs scheduled aggregation workflows.
5. Curated data is loaded into Snowflake for analytics and reporting.

## Quick start

```bash
# Provision Kafka cluster
cd terraform/modules/msk && terraform init && terraform apply

# Start event producer
python producers/src/producer.py --rate 500

# Deploy consumers
kubectl apply -f k8s/consumers/

# Trigger batch ETL
airflow dags trigger daily_events_to_snowflake
```

## Repository layout

```text
.
|-- airflow/              # DAG definitions
|-- consumers/            # streaming consumer code
|-- docker/               # container images
|-- k8s/                  # Kubernetes deployment manifests
|-- monitoring/           # Prometheus and Grafana configuration
|-- producers/            # event producer code
|-- terraform/            # MSK and Lambda infrastructure
|-- docs/                 # diagrams and supporting documentation
`-- .github/              # validation workflows
```

## What this demonstrates

- event-driven system design with both streaming and batch layers
- Kafka-based ingestion paired with Kubernetes-scale consumers
- integration of serverless components into a broader data platform
- operational thinking around monitoring, lag, and pipeline reliability
