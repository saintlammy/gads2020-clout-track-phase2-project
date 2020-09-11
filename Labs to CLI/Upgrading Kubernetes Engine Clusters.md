# GCP Command Line Interface (CLI) codes

## Lab 2 - Upgrading Kubernetes Engine Clusters

Log in to your Google Cloud account and open Cloud Shell from Google Console. 
If prompted, click Continue to provision your terminal.

Setup your project with the command below:

`gcloud config set project [project-id]` 

Use a unique project id

### -- Set up a default project
Run the following command replacing project-id with your project id
``gcloud config set [project-id]``
	
---
### -- Set a default compute zone
Get the list of available compute zones to choose from

`gcloud compute zones list`
	
Set a default compute zone
`gcloud config set compute/zone us-central1-a`

---
### -- Create a GKE cluster
`gcloud container clusters create [cluster-name] --num-nodes=1` 

### -- Get authentication credentials for your clusters
`gcloud container clusters get-credentials [cluster-name]`

### -- Upgrade your cluster
To upgrade to default cluster version 
gcloud container clusters upgrade [cluster-name] --master
	At prompt, type Y for yes, then Enter to continue

To upgrade to a specific cluster version, choose from the list of versions, enter this command:

`gcloud container clusters get-server-config` 

*(This will display list of available cluster versions to choose from)*

Next execute the following command
`gcloud container clusters upgrade [cluster-name] \
--master --cluster-version [cluster-version`


### -- Upgrade the Node Pool in your Cluster
`gcloud container clusters upgrade [cluster-name] \
--node-pool=[node-pool-name]`

*At prompt, Type Y for yes, then Enter to continue.*

Cluster is upgraded!
