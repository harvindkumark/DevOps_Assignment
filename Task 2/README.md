**Part 2: Infrastructure**

Production Environment that allows developers to self-manage application deployments.

**Technologies and Tools:**

**GitLab-CI:** Provides CI/CD pipelines for automated building, testing, and deployment. Developers can manage their deployments via GitLab pipelines by pushing code changes to Git repositories.

**Flux:** Automates Kubernetes deployments based on changes to Git repositories (GitOps). Developers commit changes to configuration files or Helm charts in a Git repository, which Flux monitors and applies to the cluster.

**Kubernetes:** Manage and scale containerized applications. Utilize Kubernetes manifests to define and manage the state of applications.

**Vault:** Securely manages secrets and injects them into applications. 

**Ceph:** Provides scalable storage solutions for stateful applications.

**RBAC:** Ensures that developers and operations teams have fine-grained permissions based on their roles. For example, developers can deploy to production but not access sensitive data unless explicitly allowed.

**Prometheus:** Collects and stores metrics for monitoring.

**Grafana:** Visualizes metrics collected by Prometheus and provides dashboards and alerting.

The underlying infrastructure and network components are excluded from the architecture diagram as the focus is on enabling developers to self-manage application deployments.

The infrastructure can be provisioned/managed via Terraform and Ansible.

**Terraform:** Automates the underlying infrastructure, deployment of the Kubernetes cluster, including networking, storage, and security configuration. It ensures that the infrastructure is scalable and repeatable.

**Ansible:** Handles configuration management and post-deployment tasks like configuring monitoring tools, etc
