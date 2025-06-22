# Amazon Elastic Kubernetes Service (EKS)

- A managed Kubernetes (k8s) orchestration service provided by AWS.
- EKS manages the Kubernetes control plane, so you don't have to handle tasks like:
    - Control plane updates and patching
    - High availability and multi-AZ setup for the control plane
    - Scaling the control plane components
    - Backups for the control plane

### High-Level EKS Workflow
1.  **Create an EKS Cluster:** This provisions the managed Kubernetes control plane.
2.  **Configure Worker Nodes:** Add compute capacity for your containers using EKS Managed Node Groups, AWS Fargate, or self-managed EC2 instances.
3.  **Define Security:** Configure IAM roles for service accounts (IRSA) and security groups to control access.
4.  **Configure Autoscaling:** Set up the Cluster Autoscaler for nodes and the Horizontal Pod Autoscaler for your applications.
5.  **Deploy Applications:** Use `kubectl` to deploy your containerized applications to the cluster.

---

### Option 2: Detailed & Professional Version (Recommended for Documentation)
This version is more suitable for technical documentation, a wiki, or onboarding materials. It provides more context and uses more precise terminology.

---

# Amazon Elastic Kubernetes Service (EKS)

Amazon EKS is a fully managed Kubernetes service from AWS that simplifies the process of running Kubernetes on the cloud. It allows you to leverage the power of Kubernetes without the operational overhead of managing the control plane.

### Key Features & Benefits

EKS abstracts away the complexity of the Kubernetes control plane. Compared to a self-managed Kubernetes cluster, AWS handles:

-   **Managed Control Plane:** AWS provisions, scales, and manages the Kubernetes API server and etcd persistence layer with high availability across multiple AWS Availability Zones (AZs).
-   **Automated Updates & Patching:** EKS handles the version updates and security patching of the control plane, ensuring your cluster runs on a secure and stable version of Kubernetes.
-   **Deep AWS Integration:** Seamlessly integrates with core AWS services like:
    -   **IAM** for authentication and authorization (RBAC).
    -   **VPC** for network isolation.
    -   **Elastic Load Balancing (ELB)** for exposing services.
    -   **AWS Fargate** for serverless container execution.
-   **Secure by Default:** Leverages a shared responsibility model, providing a secure, isolated cluster environment that integrates with AWS security services.

### Core EKS Architecture

An EKS cluster consists of two primary components:

1.  **EKS Control Plane (Managed by AWS):** The Kubernetes masters (API server, scheduler, etcd) that run in an AWS-managed account.
2.  **Worker Nodes (Managed by You):** The EC2 instances or Fargate profiles that run your containerized applications. You are responsible for configuring, scaling, and maintaining these.

### Typical EKS Setup Workflow

1.  **Define Prerequisites:**
    -   Create an EKS Cluster IAM Role.
    -   Create an EKS Node IAM Role.
    -   Set up a VPC with public and private subnets.

2.  **Create the EKS Cluster:**
    -   Use the AWS Console, CLI, or an IaC tool like Terraform or `eksctl`. This step provisions the control plane.

3.  **Launch and Configure Worker Nodes:**
    -   **EKS Managed Node Groups:** The recommended approach. AWS handles the provisioning and lifecycle management of EC2 nodes.
    -   **AWS Fargate:** A serverless compute option where you don't manage any servers.
    -   **Self-Managed Nodes:** You manually provision and manage EC2 instances to join the cluster.

4.  **Establish Cluster Connectivity:**
    -   Configure `kubectl` to communicate with your new cluster's API server endpoint.

5.  **Deploy Add-ons and Applications:**
    -   Install essential add-ons like the **Cluster Autoscaler**, **Metrics Server**, or **AWS Load Balancer Controller**.
    -   Deploy your containerized applications using Kubernetes manifests (`.yaml` files).