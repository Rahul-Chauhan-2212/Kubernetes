# Kubernetes

<i>
<a href="https://kubernetes.io/">Kubernetes</a>
<h5>Independent Container Orchestration</h5>
<p>Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.</p>

##### Problems with Manual Deployment

<ul>
<li>Manual Deployment of containers is hard to maintain, error-prone and annoying. These issues are beyond the security and configuration concerns.</li>
<li>Containers might go down/crash and need to be replaced.</li>
<li>We might need more containers when traffic spikes.</li>
<li>Incoming traffic should be distributed equally.</li>
</ul>

##### Why Kubernetes

<ul>
<li>Container health-checks and re-deplyoment</li>
<li>Auto-scaling</li>
<li>Load Balancer</li>
</ul>
<p>Note: These all problems are solved if we use AWS ECS, but we are locked to AWS. If we want to migrate to Azure or other cloud container service provider, then we have to learn about that service.</p>

##### What Kubernetes is NOT

<ul>
<li>a cloud provider - a cloud provider service (though cloud provider might offer Kubernetes-specific services)
</li>
<li>a tool or service that manages infrastructure - Kubernetes will NOT create and launch anymachines or do anything like that (managed Kubernetes services by cloud providers might dothat)</li>
<li>a single tool or software - Kubernetes is a collection of concepts and tools</li>
</ul>

##### What is Kubernetes exactly

An open-source system(de-facto standard) for orchestrating container deployments. Helps us in below tasks:

<ul>
<li>Automatic Deployment</li>
<li>Scaling and Load Balancing</li>
<li>Management</li>
</ul>
<b>Kubernetes Configuration:</b> <span>Standardized way of describing the to-be-created and to-be-managed resources of Kubernetes Cluster</span></br>
<b>Kubernetes is like Docker Compose for Multiple Machines</b>

#### Kubernetes Core Components

<ul>
<li><b>Cluster: </b>A set of Node machines which are running the Containerized
Application (Worker Nodes) or control other Nodes (Master Node)</li>
<li><b>Nodes: </b>Physical or virtual machine with a certain hardware capacity which
hosts one or multiple Pods and communicates with the Cluster
<ol>
<li><b>Master Node: </b>Cluster Control Plane, managing the Pods across Worker Nodes</li>
<li><b>Worker Node: </b>Hosts Pods, running App Containers (+ resources)</li>
</ol>
</li>
<li><b>Pods: </b>Pods hold the actual running App Containers + their required
resources (e.g. volumes).</li>
<li><b>Containers: </b>Normal (Docker) Containers</li>
<li><b>Services: </b>A logical set (group) of Pods with a unique, Pod- and Containerindependent
IP address</li>
</ul>


### Kubernetes in Action : Diving into Core Concepts

<h5> Kubernetes' Work</h5>
<table>
<tr>
<th>What Kubernetes Does</th>
<th>What You have to Do</th>
</tr>
<tr>
<td>Create your objects(Pods) and Manage them</td>
<td>Create the Cluster and the Node instances(Master and Worker Nodes)</td>
</tr>
<tr>
<td>Monitor Pods, re-create them, Scale Pods</td>
<td>Setup API server, kubelet and other Kubernetes services/softwares on nodes</td>
</tr>
<tr>
<td>Kubernetes utilizes the provided resources to apply your configuration/goals</td>
<td>Create other(cloud) provider resources that might be needed(File Systems and Load Balancers)</td>
</tr>
</table>

<h5>Kubernetes: Required Setup and Installation Steps</h5>
<ul>
<li><b><a href="https://kubernetes.io/docs/reference/kubectl/">kubectl</a></b>A command line tool to send instructions to Kubernetes Cluster(Mainly Master Node) using Kubernetes APIs</li>
<li><b><a href="https://minikube.sigs.k8s.io/docs/start/">minikube</a></b>A local Kubernetes, focusing on making it easy to learn and develop for Kubernetes</li>
</ul>

<ul>
<b>Installation Steps links</b>
<li><a href="https://minikube.sigs.k8s.io/docs/start/">minikube</a></li>
<li><a href="https://kubernetes.io/docs/tasks/tools/#install-on-windows-using-chocolatey-or-scoop">kubectl</a></li>
</ul>
</i>
