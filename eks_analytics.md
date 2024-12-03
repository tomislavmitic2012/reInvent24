### EKS as a data platform for analytics

##### 12/03/2024

* Big data challenges
    * expliosion of data
    * Everyone uses data

* Data Personas
    * Data exposed to users
    * Batched data 
    * Historical data
    * Real time data

* 1st gen okatform target applicaitons
    * Dev team
    * platform team
* Ownership boundaries
    * Innovation vs standaridization, governance, security, stability

* Striking the balance
    * Platform Engineering

* Data scientists and Engineers
    * stateful apps
    * notebooks
    * data lakes and meshes
    * parallel processsing
* What the storage to use, type of GPU

* Goals for data workloads
    * high scalability
    * better resource utilization
    * computer/storage options
    * security and multi-tennant isolation
    * cost efficiency
* Common Challenges
    * Scaling intensive workloads
    * Fault tolerance
    * Batch scheduling
    * Logging and monitoring
    * Network
    * Mutlitenancy
    * chosing right resources
* Different options
    * Self managed Spark on EKS
    * Amazon EMR on EKS
    * Amazon EMR Serverless

* Data Platform Lifecycle

* Analytics workloads into Kubernetes
    * Traffic patterns for analytics workloads is spurty and sporadic
    * You will need to optimize your EKS cluster

* Avoid overlay networks due to the latency

* Core DNS needs to scaled via managed scaling

* Build Prod-Ready EKS cluster
    * 1st Layer
        * Networking
        * VPC CNI
        * Core DNS
        * Karpenter
        * Storage
        * AWS ECR
        * Monitoring
    * 2nd Layer
        * Purpose built cluster
        * Apache Flink or Apache Spark
        * Yunicorn
        * Apache Airflow or Argo Workflows
    * 3rd Layer
        * Tennant Isolation
        * Automaiton
        * Use of Kubernetes API and extending the Kubernetes API
            * AWS Controllers for Kubernetes (ACK)


