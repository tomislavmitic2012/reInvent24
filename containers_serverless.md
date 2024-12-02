### Containers or Serverless

#### Session 12/01/2024

* Typical containerized application
    * Application Load Balancer
    * Orchestration
        * Container runtime
        * cmopute node
    * Application Code
    * Framework
    * HTTP Server

* Server Based Containers
* App Load Balancer
* NAT gateway
* Amazon EC@
    * Cluster autoscaling with Karpenter

* Familiar Env with broad choice of open source projects
* Full control and debugging capabilities
* Flexibility of Infrastrucutre
* Responsibility of cluster operations, upgrades and maintenance

* Serverless
* Serverless is not a specific technology

* AWS Fargate
    * Allows us to scale on up to date runtimes on a single compute tennant
    * Helps to autoscale our workloads

* AWS Fargate reduces our responsibility

* AWS App runner helps us take out the networking layer so we have less responsibility

* Containers or Serverless Functions
* AWS Lambda
* You are not directly calling your lambda function
* Lambda Service is invoking the function

* Lambda Event Source Mappings
    * Lambda is responsible for polling your SQS queue and invokes your methods
    * It is aware of queue depth

* Lambda Scaling
    * Scales to 0
    * execution envs can be shut down after inactivity
    * fine granualr managed auto-scaling
* initialization --> Execution (Cold Start) --> Execition (Warm Start) --> Initilizagion --> Execution 
* 5 min time limit for the executions

* The processing of a request or an event is a unit of work for a container, but it is THE unit of work for a function
* Lambda doesn't run if there is no work

* Invoking multiple functions
* Will I end up with hundreds of functions
* Lambda function can have different HTTP methods
* Lambda function can use api gateway and call different handler endpoints in the lambda function

* When to choose what?
* Operations from full controll to fully managed
* Containers offer great flexibility
    * runtime
    * deployment flexibility
* Function
    * provide simplicity

* Containers: Integration from flexibility to simplicity
* Function: fkexibility with integration

* Integration vs Portability
* Container vs Function
    * containers are flexible (liberal inbound and outbound communication)
* Lambda
    * Invoked by the service
    * Inbound communication and schema defined by service
    * Outbound communication is flexible
* Orchestration of containers is more complex
    * must consider this with portability
* Function can be packaged and handed off to a different Function Invocation Service or container Orchestrater
* Leverage existing container toling
* Official AWS Kmabda image base
* custom images must comunicate with the Lambda service

* lambda and JSON payload
    * specific JSON payload is received
    * Reuse HTTP framework routing
    * awslabs/aws-lambda-web-adapter
    * aws/serverless-java-container

* The decision when to use containers or functions is mainly workload being processed
* Container pricing
    * Cost efficient for high, constant, or predicatble loads
    * Optimize via spot instances, Saving Plans, and Reserved Instances
    * Operational cost depends on abstraction

* AWS Lambda pricing
    * based on usage milliseconds
    * cost efficient for spiky and variable workloads
    * Scale to zero = zero cost
    * low operation overhead
    * ver efficient

* You need to know your work patters and make the informed decision about whether to use containers or functions


