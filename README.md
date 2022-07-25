# Kubernetes

### Kubernetes Introduction
<i>
<a href="https://kubernetes.io/">Kubernetes</a>
<h5>Independent Container Orchestration</h5>
<p>Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.</p>

#### Problems with Manual Deployment

<ul>
<li>Manual Deployment of containers is hard to maintain, error-prone and annoying. These issues are beyond the security and configuration concerns.</li>
<li>Containers might go down/crash and need to be replaced.</li>
<li>We might need more containers when traffic spikes.</li>
<li>Incoming traffic should be distributed equally.</li>
</ul>

#### Why Kubernetes

<ul>
<li>Container health-checks and re-deplyoment</li>
<li>Auto-scaling</li>
<li>Load Balancer</li>
</ul>
<p>Note: These all problems are solved if we use AWS ECS, but we are locked to AWS. If we want to migrate to Azure or other cloud container service provider, then we have to learn about that service.</p>

#### What Kubernetes is NOT

<ul>
<li>a cloud provider - a cloud provider service (though cloud provider might offer Kubernetes-specific services)
</li>
<li>a tool or service that manages infrastructure - Kubernetes will NOT create and launch anymachines or do anything like that (managed Kubernetes services by cloud providers might dothat)</li>
<li>a single tool or software - Kubernetes is a collection of concepts and tools</li>
</ul>

#### What is Kubernetes exactly

An open-source system(de-facto standard) for orchestrating container deployments. Helps us in below tasks:

<ul>
<li>Automatic Deployment</li>
<li>Scaling and Load Balancing</li>
<li>Management</li>
</ul>
<b>Kubernetes Configuration:</b> <span>Standardized way of describing the to-be-created and to-be-managed resources of Kubernetes Cluster</span></br>
<b>Kubernetes is like Docker Compose for Multiple Machines</b>

<hr>

### Kubernetes Core Components

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

<hr>

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
<ol>
<li><b><a href="https://kubernetes.io/docs/reference/kubectl/">kubectl</a></b> A command line tool to send instructions to Kubernetes Cluster(Mainly Master Node) using Kubernetes APIs</li>
<li><b><a href="https://minikube.sigs.k8s.io/docs/start/">minikube</a></b> A local Kubernetes, focusing on making it easy to learn and develop for Kubernetes</li>
</ol>

<ul>
<b>Installation Steps links</b>
<li><a href="https://minikube.sigs.k8s.io/docs/start/">minikube</a></li>
<li><a href="https://kubernetes.io/docs/tasks/tools/#install-on-windows-using-chocolatey-or-scoop">kubectl</a></li>
</ul>

<h6>Start Minikube using Docker</h6> 
<h5>minikube start --driver=docker</h5>
<h6>To check status of cluster</h6>
<h5>minikube status</h5>
<h6>To open Minikube Browser Dashboard</h6>
<h5>minikube dashboard</h5>
<h6>To delete Minikube cluster</h6>
<h5>minikube delete</h5>

<p>Kubernetes works with <b>Objects</b></p>
<h5>Objects</h5>
<ul>
<li>Pods</li>
<li>Deployments</li>
<li>Service</li>
<li>Volumes</li>
</ul>

<h5>Objects can be created in two ways</h5>
<ul>
<li>Imperatively</li>
<li>Declartively</li>
</ul>

<h5>The "Pod" Object</h5>
<p>The smallest unit Kubernetes interacts with</p>
<ul>
<li>Contains and runs one or multiple containers(mainly one container per pod)</li>
<li>Pod contains shared resources(volumes) for all Pod containers</li>
<li>Has a cluster internal IP by default(containers inside a Pod can communicate via localhost)</li>
</ul>
<p><b>Pods are designed to be ephemeral: Kubernetes will start, stop and replace them as needed.</b></p>
<p>For Pods to be managed for you, you need a <b>Controller(i.e Deployment)</b></p>

<h5>The "Deployment" Object</h5>
<p>Controls(Multiple) Pods</p>
<ul>
<li>You set a desired state, Kubernetes then changes the actual state
<p>Define which pods and container to run and number of instances</p</li>
<li>Deployments can be paused, deleted and rolled back</li>
<li>Deployments can be scaled dynamically(and automatically)</li>
</ul>
<p><b>Deployments manage a Pod for you, you can also create deployments.</b></p>
<p><b>You therefore don't directly control the Pods, instead you use deployment to set up the desired end state</b></p>

<hr>

#### A First Deployment using Imperative approach

Project used ---> <a hrefd="https://github.com/Rahul-Chauhan-2212/Kubernetes/tree/main/kub-action-starting-up"><b>kub-action-starting-up</b></a>

<ul><b>Commands used to create first deployment</b>
<li>
<h6>kubectl create deployment name-of-deployment --image=image-name-with-repo-on-dockerhub</h6>
<p>Used to create deployment on the basis of an image on Docker registry. kubectl create deployment first-app --image=rchauhan9102/kub-first-app</p>
</li>
<li>
<h6>kubectl get deployments</h6>
<p>Used to get the deployments and their info</p>
</li>
<li>
<h6>kubectl get pods</h6>
<p>Used to get the pods and their info</p>
</li>
<li>
<h6>kubectl delete deployment name-of-deployment</h6>
<p>used to delete deployment and in result pods are also deleted. kubectl delete deployment first-app</p>
</li>
</ul>

<h6>kubectl: Behind the Scenes</h6>
<p>
<b>kubectl create deployment name-of-deployment --image=image-name-with-repo-on-dockerhub</b>
</br>
Commands goes to Master Node(Control Plane) ---> Scheduler analyses currently running pods and find the best node(Worker node) for our pod which is free or doing the least work. kubelet manages Pods and Containers.
</p>

<h5>The "Service" Object(Resource)</h5>
<p>Exposes Pods to the cluster or externally</p>
<ul>
<li>Pods have an internal IP address which changes when the Pod is replaced
<p>Finding Pods is hard if the IP address changes all the time</p>
</li>
<li>Service group a Pod with a shared IP address</li>
<li>Services can allow external access to Pods
<p>The default(internal only) can be overwritten</p>
</li>
</ul>
<p><b>Without services Pods are very hard to reach and communication is difficult</b></p>
<p><b>Reaching ad Pod from outside of the cluster is not possible at all without services</b></p>

### Exposing a deployment with a service

<ul><b>Commands used to expose deployment with service</b>
<li>
<h6>kubectl expose deployment first-app --type=LoadBalancer --port=8080</h6>
<p>This command exposes the deployment first-app on port 8080 create service with type LoadBalancer to so that we can get a shared IP which can be accessed from outside of the cluster.</p>
</li>
<li>
<h6>kubectl get services</h6>
<p>used to get the list of services available</p>
</li>
<li>
<h6>minikube service first-app</h6>
<p>exposes the deployment using the service to the localhost machine. This command is not required if we are running the kubernetes cluster on a Cloud provider</p>
</li>
</ul>

<h6>Types of Service Objects</h6>
<ul>
<li>ClusterIP
<p>IP address only available to Kubernetes Cluster</p>
</li>
<li>NodePort
<p>IP address of the Worker node(Machine IP at which Worker node is running)</p>
</li>
<li>LoadBalancer
<p>Shared IP for all the services and available to outside of the cluster</p>
</li>
</ul>

### Restarting Containers

<p><b>If there is any error in the running container, the Kubernates will restart the container as well as Pod</b></p>

### Scaling in action

<h6>kubectl scale deployment/first-app --replicas=3</h6>
<p>create replicas of the first-app pod</p>

### Updating Deployments

<ul><h5>### Steps</h5>
<li>Build new image with latest source code and the incrementing tag</li>
<li>Push the image with new tag to dockerhub</li>
<li><h5>kubectl set image deployment/first-app kub-first-app=rchauhan9102/kub-first-app:1</h5>
<p>to update the deployment with newly pushed docker image on dockerhub</p>
</li>
<li><h5>kubectl rollout status deployment/first-app</h5>
<p>to get the rollout status of updated deployment</p>
</li>
</ul>
<p>To make kubernetes pull the image, there should be change in new image tag</p>

### Deployment Rollbacks and History

<ul>
<li><h6>kubectl rollout undo deployment/first-app</h6>
<p>To undo the latest deployment and rolled back to the previous one</p>
</li>
<li><h6>kubectl rollout history deployment/first-app</h6>
<p>To get the history to the deployment</p>
</li>
<li><h6>kubectl rollout history deployment/first-app --revision=6</h6>
<p>To rollback to a specific deployment</p>
</li>
</ul>

<ul><h6>Deletion Commands</h6>
<li>kubectl delete service first-app</li>
<li>kubectl delete deployment first-app</li>
</ul>

#### The Imperative vs Declarative approach

<table>
<tr>
<th>Imperative</th>
<th>Declarative</th>
</tr>
<tr>
<td>kubectl create deployment ..</td>
<td>kubectl apply -f config.yaml</td>
</tr>
<tr>
<td>Individual commands are executed to trigger certain kubernetes actions</td>
<td>A config file is applied and used to change the desired state</td>
</tr>
<tr>
<td>Comparable to using docker run only</td>
<td>Comparable to using docker compose with compose files</td>
</tr>
</table>

### Declarative Deployment

<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.24/"><b>Reference Doc to create yaml file for Declarative Approach</b></a>

<ul>
<li><h5>kubectl apply -f=deployment.yaml</h5>
<p>Used to apply the deployment related changes</p>
</li>
<li><h5>kubectl apply -f=service.yaml</h5>
<p>Used to apply the service related changes</p>
</li>
<li><h5>kubectl delete -f=deployment.yaml,service.yaml</h5>
<p>Used to delete the deployment and services</p>
</li>
</ul>
<p>To update the deployment we just have modify the yaml file and apply those changes</p>
<p>Labels and Selectors are necessary... Labels and Selectors are used to make a link between pods and services</p>

<p>We can have multiple resources in one single deployment file by adding --- in yaml file. It is better pratice to create service before deployment.</p>

##### More on Labels and Selectors

<ul>
<li>
<p>
<b>
matchExpressions:</br>
  - key: app</br>
    operator: In</br>
    values:</br>
      - second-app</br>
      - first-app
</b>
We can use matchExpressions in place of matchLabels to select on the basic of key value pair and operator.
</p>
</li>
<li>
<h6>kubectl delete -l labelKey=labelValue deployments,services</h6>
<p>Used to delete the resoures on the basis label key value defined in applied config file</p>
</li>
</ul>

##### Liveness Probes

<ul>
<li>
<b>
livenessProbe:</br>
  httpGet:</br>
    path: /</br>
    port: 8080</br>
  periodSeconds: 10</br>
  initialDelaySeconds: 5
</b>
<p>Used to get the health of the running container</p>
</li>

#### Configuration Options

<ul>
<li>
<h5>imagePullPolicy: Always</ul>
<p>Force kubernetes to pull the image always during update in deployment</p>
</li>
</ul>

<hr>

### Managing Data and Volumes with Kubernetes

<ul>
<h5>State</h5>
<p>State is data created and used by your application which should not be lost</p>
<li>
<h6>User-generated data, user-accounts</h6>
<p>Often stored in databases but can also be file(e.g. Upload files)</p>
</li>
<li>
<h6>Intermediate results derived by the app</h6>
<p>Often stored in memory, temporary database tables or files</p>
</li>
</ul>

#### Kubernetes and Volumes

<ul>Kubernetes can mount volumes into containers
<li>A broad variety of volumes/driver types are supported
<ol>
<li>Local Volumes(i.e. On Nodes)</li>
<li>Cloud provider specific volumes</li>
</ol>
</li>
<li>Volume lifetime depends on the Pod lifetime
<ol>
<li>Volume survives containers re-starts(and removal)</li>
<li>Volumes are deleted if the Pods are destroyed</li>
</ol>
</li>

#### Kubernetes Volumes vs Docker Volumes

<table>
<tr>
<th>Kubernetes Volumes</th>
<th>Docker Volumes</th>
</tr>
<tr>
<td>Supports many different drivers and Types</td>
<td>Basically no driver/type support</td>
</tr>
<tr>
<td>Volumes are not necessarily persistent</td>
<td>Volumes persists until manually cleared</td>
</tr>
<tr>
<td>Volumes survives container restarts and removal</td>
<td>Volumes survives container restarts and removal</td>
</tr>
</table>
</ul>

#### Getting started with Kubernetes Volumes

<b><a href="https://kubernetes.io/docs/concepts/storage/volumes/">Kubernetes Volumes Documentation</a></b>

<ul>Some Common Kubernetes volume types
<li><h5>emptyDir</h5>
<p>Creates an empty directory and is linked with a container path so content can be written and saved at the newly created empty directly in Worker Node. It is not suitable for multiple replicas.</p>
</li>
<li><h5>hostPath</h5>
<p>Used for Multiple Replicas. It stores data in host machine(Worker Node) and available for all replicas.</p>
</li>
<li><h5>csi (Container Storage Interface)</h5>
<p>Used for any outside file system which is very flexible. You just need integration driver available for that file system.</p>
</li>
</ul>

#### Persistent Volumes

<p>Volumes are destroyed when a Pod is removed.
<b>hostPath partially work around that is one-node environments like minikube</b>
</p>
<h5>Pod- and Node-dependent volumes are sometimes required.--->Persistent Volumes</h5>

<b><a href="https://kubernetes.io/docs/concepts/storage/persistent-volumes/">Persistent Volumes</a></b>

<h5>"Normal" Volumes vs Persistent Volumes</h5>
<table>
<tr>
<th>"Normal" Volumes</th>
<th>Persistent Volumes</th>
</tr>
<tr>
<td>Allows to persist Data</td>
<td>Allows to persist Data</td>
</tr>
<tr>
<td>Volume is attached to Pod and Pod Lifecycle</td>
<td>Volume is a Standalone Cluster Resource(Not attached to a Pod)</td>
</tr>
<tr>
<td>Defined and Created together with Pod</td>
<td>Created standalone and claimed via PVC</td>
</tr>
<tr>
<td>Repetitive and hard to administer on a global level</td>
<td>Can be defined once and used multiple times</td>
</tr>
<table>

<ul><h5>Steps to create Persitent Volumes</h5>
<li>Define a Persistent Volume</li>
<li>Define a Persistent Volume Claim</li>
<li>Using a Claim in Pod</li>
</ul>

<ul><b>Commands for Persistent Volume Deployment</b>
<li>
<h5>kubectl get sc</h5>
<p>To get the Storage Classes</p>
</li>
<li>
<h5>kubectl apply -f="host-pv.yaml"</h5>
<p>To apply Persistent Volume Config</p>
</li>
<li>
<h5>kubectl get pv</h5>
<p>To get the List of Persistent Volumes</p>
</li>
<li>
<h5>kubectl apply -f="host-pvc.yaml"</h5>
<p>To apply Persistent Volume Claim</p>
</li>
<li>
<h5>kubectl get pvc</h5>
<p>To get the List of Persistent Volume Claims</p>
</li>
<li>
<h5>kubectl apply -f="deployment.yaml"</h5>
<p>To update the deployment</p>
</li>
</ul>

#### Environment Variables

<p>We can set using env tag at containers tag in deployment.yaml</p>

<ul>
<li>
<h5>kubectl apply -f="environment.yaml"</h5>
<p>To Apply config Map</p>
</li>
<li>
<h5>kubectl get configmap</h5>
<p>To get Config Map</p>
</li>
</ul>

<hr>

### Kubernetes Networking

</i>
