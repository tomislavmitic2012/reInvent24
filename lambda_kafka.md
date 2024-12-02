##### AWS Lambda and Apache Kafka for real-time data processing applications

###### 12/2/2024 10 am PST

* [Slides](https://serverlessland.com/reinvent2024/svs321)

* AWS and Apache Kafka for realt time data processing 
* Data streaming on AWS
* Architecture of streaming data
* Kafka Streaming Data with Lambda

* Before data was siloed
* Modern day data architecutre is far more connected

* Batch Processing vs Streaming Processing
* Hourly server logs vs real time metrics

* Common Uses
* Automation
* Online Interactions
* Data Lake
* Log Analytics
* IOT Monitoring
* Click Stream Data 

* Streaming Data Pipeline
* Stream Sources --> Stream Ingestions --> Stream Storage --> Stream Analytics --> Outcomes

* Characteristics
* High Volume
* Continuous
* Ordered
* Time-Sensitive

* Apache Kafka
* Service Bus?
* Rest or Async?
* Database?
* Does all of the above
* Streaming platform

* Running Kafka
* Self managed (premises/Cloud)
* Amazon MSK
* Confluent
* Redpanda
* WarpStream

* Amazon MSK
* Automate provisioning, configuring and tuning
* Fully compatible with open source Apache Kafka
* Highly secure
* Lower Cost
* Fully Managed

* Amazon MSK Serverless
* Flavor of Serverless 
* Pay how much data you stream and how much you will store
* Pay for data you stream and retain

* Kafka clusters, brokers, topics, partitions, records
* Broker runs and manages kafka
* Topic message channel
* Partitions partitions data for processing and throughput

* Producers put messages on a partition
* A partition is a ordred set of records
* messages put on front of the set
* Messages land on a partition based on the partition key
* Partition Assignments
    * Random Hash
    * Time-based Hash
    * Application-Specific Hash
* Kafka Offset
    * Tracks the partition record sequence
    * Consumers store this to keep trach of their portion in the stream

* Consuming Streaming records
* Processing
    * Amazon EventBridge bus
    * Amazon EventBridge Pipes
    * Lambda evnet source mapping
    * Kafka Connect

* Analytics
    * Amazon Manged Service for Apache Flink
    * AWS Glue

* Amazon EventBridge event bus
* A service event router in AWS
* Allows to filter and transform records as you need

* Kafka vs EventBridge
* Stream (pull) vs discrete events (push)
* Smart endpoints vs AWS and partner integrations
* Open source vs Low code
* Fully managed for both

* Kafka connector for Amazon EventBridge
* Open source

* EventBridge Pipes: Point-to-Point
* Kafka use case
* Connect your self managed Kafka cluster to other AWS services and HTTP APIs without writing any code

* Kafka Lambda consumer options
* Kafka sinck connector
* Lambda Event source mapping
* Either approach good since you are not writing the polling code

* Kafka Lmabda Sinck Connector
* Polls Kafka partitions and calls function synchronously or asynchronously
* At least onve semantics
* Must work in an idempotent manner
* Scales up to soft maximum of 10 connectors
* Lambda Error handling semantics follow async/sync invocations

* Lambda Event Source Mapping
* Poller source for different services
* AWS runs the pollers on you behlf
* Lambda manages to scaling
* Confugurable starting position
* Supports optional filtering
* Custom processing in any language runtime

* Event source Mapping
* AWS Lambda Service
    * poll --> filter --> filter --> batch --> invoke

* Event source mapping: starting position
    * Trime Horizon
    * At timestamp
    * Latest

* Kafka evnet source mapping: Consumer group ID
* Uniquely identifies in the consumer in the Kafka world
* Usefull in disaster recovery work loads

* Event source Mapping: Filtering
* Filter to control which messages to process by lambda
* can help to reduce costs

* Event source mapping: Batching
* Batch records together in a single payload
    * Batching window -> ampount of time to fill up the batch
    * Batch size
    * Payload size

* Event Source Mapping: Invocation
* Get the batches and invoke the Lmabda funtion

* Lmabda Authentication to Kafka
* SASL
* Amazon MSK
* Amazon MSK Serverless

* Self hosted Kafka networking
* Lambda ESM connectivity to self-hosted Kafka
    * Accesses Kafka over WAN
    * Requires NAT gateway in publuc subnects
    * 
    * Confugure subnets/security groups for access
    * Lamda function and Amazon MSK VPC can be same or different account

* Amazon MSK networking: Lambda ESM to MSK
    * Lambda ESM connectivity to Amazon MSK
    * Doesn't use function VPS settings
    * ESM creates an ENI inside each cluster subnet
    * Uses subnet//security group settings on target cluster
    * Security group rul must grant self inbound/outbound access

* Amaon MSK netowrking: VPN outbound
* MSK VPC outbound connectivity On-Demand
* VPC endpoint option
* MSK VPC requires outbound connectivity to
    * AMS Lambda
    * AWS Security Token Service
    * AMS Secrets Manager

* Amazon MSK to Lambda: Scaling
* Starts with one concurrent poller and mutliple functions
* Evaluates offset lad every minute
* Scales the number of pollers (takes 3 minutes)
* Consumers can scale up to the numebr of partitions

* Partition processing
* Default Settings
    * invokes the function with the same batch of records
    * Repeat until it succeeds or th records age out of the stream
* Failure destination
    * Send batch to the configured failure destination
        * SQS/SNS: metadata
        * S3: invocation record
    * If no failure destination is configured, they are discarded

* New Lambda and Kafka feautres: 2023-2024
* Scaling
    * faster scale-up and slower scale-down
    * Provisioned Mode
* Availability
    * On-failure destination for Kafka ESMs
* Configuration
    * Starting position timestamp for Kafka
    * ESM filtering enhancements and filter criteria encryption
    * Cross account support for MSK
    * Provisioned Mode Simplified networking

* Provisioned Mode (New)
* Provision event pollers in advance to handle suddne spikes in traffic
* For applications with stringent performance requirements
* Controls for optimize throughput
    * Minimum event pollers (1-200)
    * maximum event pollers (1-2000)
* Biling unicalled Event Poller Unit - 20 MB/s of throughput
* No longer required to configure PrivateLink or NAT Gateway

* Measuring Performance
* Stram Baseline load
    * Average rtecords per second
    * Averable bytes per second
    * INcrease in record volume per partition
    * Increase in the size of the records
* Lambda performance baseline
    * Time to process a single record
    * time to process average batch size
    * Function errors, throttles
    * Duration, invocations, retries all affect performance

* Kafka metrics/alarms
    * Basic/default monitoring
    * Enhanced Monitoring
    * Per broker/topic/partition
    * consumer_lag
    * consumer_offset

* AWS Cloudwatch metrics
    * Invocations
    * Duration
    * Error count
    * Throttles
    * Concurrency
    * OffsetLag (Kafka)

* Increasing processing throughput: Lmabda
    * Filtering
    * Increase memory allocation
    * Increase batch size
    * gracefullt handle invocation errors
    * Manage your concurrency and throttles

* Increasing processing throughtput: Stream
    * Evenly distribute records using partition key
    * Increase paritions to increase numebr of Lambda consumers
    * Buffer records at the producer side





