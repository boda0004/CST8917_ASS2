# CST8917 – Serverless Applications
## Assignment 2 – Serverless Service Alternatives Report
##  Objective
The following are some of the similarities and disparities between Microsoft Azure serverless services and its equivalent in Amazon Web services ( AWS ) and Google cloud platform ( GCP )  
The notions would be to turn the cloud provider into something you know so that one can analyze **features, triggers/bindings, integration, observability, prices, and trade-offs** of each choice.

---

##Services compared
- Azure Functions  
- Long-running functions Durable Functions  
- Azure Logic Apps  
- Azure Service Bus  
- Azure Event Grid  
- Azure Event Hubs Business Continuity/Disaster Recovery  

---

## 1. Azure Functions vs AWS Lambda vs Google Cloud Functions

| Aspect                  | Azure Functions | AWS Lambda | Google Cloud Functions |
|--------------------------|-----------------|------------|-------------------------|
| **Overview**            | Event-driven serverless compute supporting multiple languages with triggers/bindings | Serverless compute triggered by events or API Gateway | Lightweight serverless compute triggered by HTTP, Pub/Sub, or storage events |
| **Supported Runtimes**  | .NET, Node.js, Python, Java, PowerShell, Custom handlers | Node.js, Python, Java, Go, .NET, Ruby, Custom runtime | Node.js, Python, Go, Java, .NET |
| **Triggers & Bindings** | HTTP, Timer, Storage Blobs, Event Hubs, Service Bus, Event Grid | API Gateway, S3, DynamoDB, EventBridge, SQS, Kinesis | HTTP, Pub/Sub, Cloud Storage, Firestore |
| **Integration Options** | Deep integration with Azure ecosystem (Event Grid, Service Bus, Cosmos DB) | Native AWS service integrations | Strong ties to Google services (BigQuery, Pub/Sub, Firebase) |
| **Monitoring**          | Azure Monitor, App Insights | CloudWatch | Cloud Monitoring & Logging |
| **Pricing**             | Consumption plan (per execution & GB-sec) | Pay per request & execution time | Pay per request & compute time |

**Narrative:**  
Azure Functions and AWS Lambda are nearly identical with the concept, but the GCP Functions is targeted towards ease and direct integrations with Google products. Azure possesses more out of box integration modules and GCP excels on analytics workflow, whilst AWS is more scale mature.

---

## 2. Durable Functions -vs- AWS Step Functions -vs- Google Cloud Workflows

| Aspect                  | Azure Durable Functions | AWS Step Functions | GCP Workflows |
|--------------------------|--------------------------|--------------------|---------------|
| **Overview**            | Extension of Azure Functions for orchestration (chaining, fan-out/fan-in) | Workflow service that coordinates AWS Lambda and other services | Fully managed workflow orchestration |
| **Patterns Supported**  | Function chaining, fan-out/fan-in, async wait, human interaction | Sequential & parallel workflows, retries, error handling | Sequential workflows, error handling |
| **Integration Options** | Azure Functions + any Azure trigger/binding | Tight integration with AWS ecosystem (Lambda, ECS, DynamoDB) | Works with GCP APIs & services |
| **Monitoring**          | Azure Application Insights | AWS CloudWatch | Cloud Logging, Cloud Trace |
| **Pricing**             | Based on function executions and storage | Per state transition | Per workflow execution step |

**Narrative:**  
Durable Functions have a feel that is code-first (orchestration within functions) whereas AWS Step Functions are visual and declarative. GCP Workflows focuses on orchestration with APIs. Azure is geared more towards developers, AWS is good with large workflows, and GCP is easier and less functional.

---

## 3. Azure Logic Apps vs AWS Step Functions (Express) vs GCP Workflows

| Aspect                  | Azure Logic Apps | AWS Step Functions (Express) | Google Cloud Workflows |
|--------------------------|------------------|------------------------------|-------------------------|
| **Overview**            | Low-code/no-code integration workflows | Orchestration for event-driven apps | Orchestration for Google APIs and services |
| **Triggers**            | 300+ connectors (O365, Salesforce, SAP, etc.) | EventBridge, API Gateway, SQS, SNS | HTTP, Pub/Sub, Cloud Storage |
| **Integration Options** | Connectors to SaaS & enterprise apps | Tight AWS service integrations | GCP services and REST APIs |
| **Monitoring**          | Azure Monitor, Log Analytics | CloudWatch | Cloud Monitoring |
| **Pricing**             | Per action and trigger execution | Per request/state transition | Per step execution |

**Narrative:**  
The connectors mean that Logic Apps can shine in business/SaaS automation. AWS and GCP pay additional attention to cloud-native orchestration. Azure is best at integration to the enterprise; developers need AWS and GCP is light and has fewer connectors.

---

## 4. Azure Service Bus vs AWS SQS/SNS vs Google Pub/Sub

| Aspect                  | Azure Service Bus | AWS SQS / SNS | Google Pub/Sub |
|--------------------------|-------------------|---------------|----------------|
| **Overview**            | Messaging with queues & topics (enterprise-grade) | SQS (queue), SNS (pub/sub) | Pub/Sub for messaging and streaming |
| **Message Types**       | Queues & Topics (with sessions, FIFO, DLQ) | SQS: Queue, FIFO; SNS: Topic | Topic-subscription model |
| **Delivery**            | At-least-once, FIFO, DLQ support | At-least-once, FIFO (SQS), fan-out (SNS) | At-least-once, ordered delivery, DLQ |
| **Integration Options** | Logic Apps, Functions, Event Grid | Lambda, Step Functions, EventBridge | Cloud Functions, Dataflow, BigQuery |
| **Monitoring**          | Azure Monitor | CloudWatch | Cloud Monitoring |
| **Pricing**             | Per message operation | Per request | Per message volume |

**Narrative:**  
Azure Service Bus has additional enterprise capabilities (transactions, sessions, and duplicate detection). AWS decomposes queueing (SQS) and pub/sub (SNS). GCP Pub/Sub is an integration of both. Azure is highly enterprise, AWS is modular, GCP is less complex but easily scalable.

---

## 5. Azure Event Grid vs AWS EventBridge vs GCP Eventarc

| Aspect                  | Azure Event Grid | AWS EventBridge | Google Eventarc |
|--------------------------|------------------|-----------------|-----------------|
| **Overview**            | Event routing with pub/sub model | Serverless event bus for routing events | Serverless event delivery for GCP services |
| **Event Sources**       | Azure services, custom apps, SaaS | AWS services, custom events, SaaS | GCP services, Cloud Storage, Pub/Sub |
| **Delivery**            | Push to subscribers | Push to subscribers | Push to subscribers |
| **Integration Options** | Functions, Logic Apps, Service Bus, Event Hubs | Lambda, Step Functions, SQS | Cloud Functions, Workflows |
| **Monitoring**          | Azure Monitor | CloudWatch | Cloud Logging |
| **Pricing**             | Per event | Per event | Per event |

**Narrative:**  
Event Grid, EventBridge and Eventarc have similar concept. Azure and AWS offer wider event ecosystems that have SaaS hooks, whereas GCP Eventarc remains in its infancy, but is strongly coupled to GCP services.

---

# 6. Azure Event Hubs vs AWS Kinesis vs GCP Pub/Sub

| Aspect                  | Azure Event Hubs | AWS Kinesis | Google Pub/Sub |
|--------------------------|------------------|-------------|----------------|
| **Overview**            | Big data event ingestion and streaming | Real-time data streaming & analytics | Global event ingestion & streaming |
| **Use Cases**           | IoT, telemetry, log ingestion | Real-time analytics, video, logs | Analytics, IoT, big data pipelines |
| **Throughput**          | Millions of events/sec | High throughput partitions | Scales automatically |
| **Integration Options** | Stream Analytics, Functions, Databricks | Lambda, Firehose, Analytics | Dataflow, BigQuery, Functions |
| **Monitoring**          | Azure Monitor | CloudWatch | Cloud Monitoring |
| **Pricing**             | Per throughput unit + events | Shard/hour + data | Per data volume |

**Narrative:**  
Direct competitors of high throughput event ingestion are Event Hubs and Kinesis. Here GCP Pub/Sub crosses over. Azure is a better choice with Stream Analytics; AWS is a better choice with analytic stack like Firehose + analytics framework; GCP is a better choice with pipelines like BigQuery/Dataflow.

---


## 📊 Strengths & Weaknesses Summary

| Service          | Azure Strengths | Azure Weaknesses | AWS Strengths | AWS Weaknesses | GCP Strengths | GCP Weaknesses |
|------------------|-----------------|------------------|---------------|----------------|---------------|----------------|
| **Functions**    | Rich triggers & bindings, hybrid support | Slightly higher cold start latency | Mature, highly scalable | Fewer built-in bindings than Azure | Simple, strong data/ML integration | Fewer enterprise connectors |
| **Durable/Workflows** | Code-first orchestration, deep integration | Less visual than AWS | Visual workflows, strong retries/error handling | Costlier for large workflows | Simple YAML/API orchestration | Less powerful for complex workflows |
| **Logic Apps**   | 300+ connectors, SaaS integration | Higher costs at scale | Developer-friendly orchestration | Lacks SaaS connectors | Lightweight workflows, REST focus | Limited SaaS connectors |
| **Service Bus / Messaging** | Advanced enterprise features (transactions, sessions) | Complex setup, costlier | Modular (SQS, SNS), highly scalable | Split services can add complexity | Simple unified messaging | Fewer advanced features |
| **Event Grid**   | Broad ecosystem, SaaS hooks | Fewer global event sources | Broad ecosystem, SaaS + cross-account | More complex rules | Tight GCP integration | Still maturing, fewer event sources |
| **Event Hubs / Streaming** | Enterprise IoT & telemetry, Stream Analytics | Throughput unit model adds cost | Strong streaming ecosystem (Kinesis + Firehose) | Higher ops overhead | Auto-scaling global streaming | Simpler but fewer enterprise controls |

---

##Conclusion
All the cloud providers have a close analogy of the Azure serverless services. Key takeaways:

- **Azure**: Powerful on enterprise workflows, powerful connectors and hybrid.  
- AWS: Mature, modular and flexible market leader.  
- GCP: Most suitable to simplicity, analytics, and integration with Google ecosystem.  

The decision will rely on the demands of enterprises:  
Azure as connectors and hybrid enterprise workloads  
AWS of breadth, maturity, and scale  
**Analytics-based, straightforward workflows GCP** 

