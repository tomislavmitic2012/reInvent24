### EKS for Edge and Hybrid Cases

#### 12/04/2024

* Hybrid env challenges
* Standardization
* EKS can help
* EKS hybrid dive
* Next steps

* Challenges
    * Operational overhead
    * Technology Sprawl
    * Difficult to make Changes
    * Limited Skillset

* Standardization
    * Benefits
        * Align with open standards
        * Portability
        * Community innovation
        * Felxiobility/ecosystem
        * Declarative operations
    * Challenges
        * Steep learning curve
        * Operational complexity
        * Scaling challenges

* Choosing Best EKS architecture
    * Cloud connected use cases
    * AWS Outpost with EKS
    * EKS Hybrid nodes (New)
* Enterprise Modernization
* Local Data processing
* Cloud disconnected use cases
    * EKS anywhere (2021)
    * Telco
    * Financial Services
    * Travel
    * Air gapped envs

* EKS on AWS Outposts
    * Two Models
        * Extended clusters
        * Local clusters

* Extended Amazon EKS to run on AWS Outposts
    * Manaaged cloud based control plane
    * Service Link from outpost to AWS Cloud plane in VPC region
    * Outpost subnet is connected to the Cloud region VPC

* Self managed node groups in your outpost subnet
* Local Gateway from outpost to rest of data center

* EKS anywhere overview and architecture patterns
    * Overview
    * Stack of components
        * Infra providers
        * EKS Distro
        * Cluster Lifecyle Management and Cluster API, Cillium (Container Networking)
        * Amazon EKS Anywhere curated packages
            * Tools and tooling to carry out activities required to make apps available to users

* Cluster Creation and Management
    * eksctl Cli
    * Terraform
    * GitOps

* Deployment Topology
    * Stadalone Clusters
    * Management/Workload Clusters

* Cellular Cluster Management
    * 100s of kubernetes being run
    * Uses YAML based configuration

* Deployment Options
    * Multi-node clusters (each node acts as a control plane)
    * Single-node clusters (Run entire env on single bare metal node)

* Best Practices
    * User GitOps for cluster management, store configs as code
    * User curated packages
    * Cluster upgrades
    * Integrate with LDAP or OIDC
    * Leverage Cilium for pod-level networking

* EKS Hybrid Nodes
    * Customer now use on-premise and edge infrastrucutre as nodes in EKS clusters for unified K8s management across envs
    * Enable your systems tp connected to the EKS control plane

* nodeadm: hybrid nodes command line interface (CLI)
* Runs on the on-prem nodes to connect and manage your on-prem systems with the EKS cloud control plane
* Responsibilities b/t AWS EKS and Hybrid nodes
    * AWS supports on prem integration to EKS control plane
    * Customers manage their bare metal nodes

* Traffic Routing to on-prem
    * config node network CIDR
    * config Pod network CIDR
    * CIDR ranges cannot overlap



 
