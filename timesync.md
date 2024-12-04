### Amazon TimeSync

#### 12/04/2024

* Clocks in dirstributed systems
* Microsecond accuracy in AWS
* Amazon Aurora Limitless

* Clocks as a primitive for improve a system
    * Ordering of events in distributed systems computing is fundamental and important
    * As the world gets more complex trusted clocks are simpler, streamlined solution
        * One-way latency measurements
        * point in time snapshots

* Clock Trustworthiness
    * AWS Time Sync service
    * Built on the AWS Nitro system
    * Supported in 5 AWS regions
    * Supported on hundreds of EC2 instance types
    * 1st and only microsecond precision
    * No additional cost
    * Prcision Time Protocol
    * Network Time Protocol

* Reliable methods to compare and order timestamps of events across hosts
* Give current time and range of error
* Open source project
* Applications
    * Auditing of clock accuracy on your whole infrastructure
    * Trace and ordert event logs in distributed systems

* Amazon Aurora Limitless and Amazon Aurora DSQL
    * ACID: Isolation defines concruency for transactions
    * Precise clocks save latency in reducing complexity



