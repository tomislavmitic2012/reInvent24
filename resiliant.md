### Building, operating, and testing resilient Multi-AZ applications

#### 12/05/2023

* Single az failures - Grey Failures
* Designing resiliant AZs

* Grey Failures
    * Differential Observability
    * Underlying system might not see impact
    * From other's viewpoint it is failing

* System vs Customer Perspective
    * System perspective healthy
    * Customer perspective unhealthy

* Fault Boundaries
    * Region
    * Availability Zone
    * Instance containers
    * Software module or system component

* AZ Independence
    * if one AZ has problems the other AZ can still process the requests

* Testing 
    * AWS Fault injection service
    * Chaos engineering

* Detecting AZ failutes
    * Can rely on health checks
    * Only one health check path
        * Multiple deps are not checked
    * Health checks may not detect grey failures
* Is there impact
* One AZ is an outlier
* Impact isn't caused by single instance

* Detection tools
    * Cloudwatch contributor Insights
    * Cloud watch alarms with Cloudwatch metric math
    * Compare logs against rules you define

* Amazon CloudWatch composite alarms
    * Combine alarms with simple logic expressions

* Outlier Detection
    * Is the AZ an outlier

* How much different is a problem
    * What is the skew in errors
    * Use Kai Square to find the skew outlier

* Can you default metrics as well from Load Balancer

* When a gray failure happens
    * Shift away from AZ

* Build AZI to prevent cascading failure
* Detect scope of impact
* Understand skew
* Create simple, reliable recovery
* Minimize configuration
* Test recovery mechanisms



