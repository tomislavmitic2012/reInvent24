### Data Pipelines on EKS

#### 12/04/2024

* Highly Scalable, cost efficient and fault tolerant pipelines are challenging
* Data and data pipelines
* Characteristics of highly scalable, efficient data pipelines

* Companies collect a lot of data
* Data pipelines have various reqs
    * Point in time snaps
    * Security
    * can't access as needed for analysis
 
 * Stages
    * Ingestion
    * Processing
    * Storage
    * Consumption

* Characterisitcs
    * Real time
    * Elastic scalability
    * Highly Available and fault tolerant

* How to Achieve
    * Run on EKS
        * Scalable
        * Better resource utilization
        * Accessible
        * Loggin and Metrics
        * Portability
        * Storage and compute options
        * cost effective
        * open source tools

* Spark on EKS
    * can me run EMR on EKS
    * EMR is service for running spark on EKS
    * Engine Support
    * Differential performance
    * Flexible job submission options 
    * Cost effective, secure, supports open table formats

* Spark run on open source
    * Want to manage stack from top to bottom since EMR doesn't give enough flexible
    * Use spark operator to make spark run easier on kubernetes

* Architectural Decisions
    * Pipelines
    * Managed
    * Compute
    * Storage
    * Network
    * Tenancy
    * Scheduling
    * Observability

* Pipeline stages
* Source systems
    * ERP
    * Streeaming
    * Own/3rd party
* Ingest
    * Flink
    * Nifi
* Transform
* Serve

* Raw Data (Landing Zone Data) --> Transform --> Currated Data (Golden Data)

* Deciding Process
    * EMR or Open Source Tools
    * EMR
        * Managed
        * Preconfigured Containers
        * Performance Optimized
    * Open Source
        * OSS (Open Source Spark) and Spark Operator
        * Makes it K8s native
    * Spark Application is created as a custom Resource

* Compute Options
    * EKS control plain is managed by AWS
    * Spark Jobs have to be scheduled
        * Driver gets scheduled first
        * Submitted as a YAML file
        * Driver Requests Executor Pods
            * Managed Node Groups
            * Karpenter
        * Cost Optimization is a factor
            * Number of pods run in 1000s
            * On demand instances
            * Spot Instances
        * Driver should be run on an on demand instance
        * Configs for driver and Executors are defined in the Karpenter Configuration

* Storage
    * 2 options
        * NVME SSD
            * high bandwidth low latency
        * EBS volumes

* Data Lake === S3

* Networking
    * Considerations
        * IP Per Pod
        * CNI can be configed to tell VPC to provide IPs to pods and run pods as 1st class citizens
        * Can exhaust your subnets
            * Need to think about your CIDR and subnet sizing
        * Can add multiple cidrs to VPCs 
            * 100.164
        * Consider the impacts of cross AZ data transfer
            * Can run a job in a single AZ
            * Use availbility zones 
            * Pod affinity
            * Node affinity
            * Instance Size and max through put and bandwidth
                * Network shaping can happen (traffic is slowed down)

* Tenancy
    * Considerations
        * Different landing and transform zones
        * How to deal with multi tenancy
            * Need to make most efficient use
            * Create another cluster to deal with this (easiest)
                * can run into multi cluster management problems as you scale up
            * How to use a single cluster to host multiple tenants
                * Using namespaces
                * Need to use role based access controls
                * IAM roles for service accounts and pod identities
            * Assign roles for different s3 buckets
            * Noisy Neighbors
                * OOM killer
                * Tennants have their own node pool with karpenter

* Scheduling
    * Kube scheduler (not designed for data analytics work loads)
        * not great for batch use cases
    * Volcano and Unicorn to schedule spark jobs
    * Benefits (Batch)
        * gives priorities to spark jobs
        * Gang scheduling (all or nothing setup)
    * Fair scheudling and FIFO ordering
    * Job scheduling
        * Run spark jobs in parallel
        * Gitops (Argo Workflows)

* Observability
    * Most exciting part :(
    * SHS (Spark History Server)
        * Spark run with a command line flag
        * Run in each tennant namespace
            * output logs to s3 bucket
    * Use an SHS helm chart
    * AWS Cloudwatch (single pane of glass)
        * allows for better cost attribution
        * split cost allocation data

