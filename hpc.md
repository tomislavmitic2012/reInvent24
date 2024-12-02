### How to configure an HPC cluster on AWS

#### Session on 12/2/2024

* Backer Hughs and Toyota uses HPC cluster on AWS
* have shown > 90% reduction in carbon footprint

* 3 pillars of HPC
    * Storage
       * Use appropriate storage for your workloads
       * Don't duplicate data
       * use shared file system b/t the computing nodes
       * Delete EBS volumes when not needed
       * Manage object lifecycle
    * Compute
        * Align resources consumption to users' demand
        * Find the best EC2 instance for each workload
        * Turn off computing nodes when not in use
    * Network
        * Use VDI solution to reduce the data movement
        * Select region on users' location
        * Use Amazon DCV

* Amaon FSx for Lustre
    * Fully managed shared storage built on the worlds most popular high-performance file system

* AWS ParallelCluster
    * one stop shop to set up your HPC cluster

* Continuous monitoring: AWS carbon footprint tool
* Calcualte carbon emissions generated from your AWS workloads
* Understand historical carbon footprint and review chages in emmision usage


