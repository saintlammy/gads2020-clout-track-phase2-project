# GCP Command Line Interface (CLI) codes

## Lab 3 - App Dev: Setting Up a Development Environment v1.1

Log in to your Google Cloud account and open Cloud Shell from Google Console. 
If prompted, click Continue to provision your terminal.

Setup your project with the command below:

```
gcloud config set project [project-id]
``` 

Use a unique project id

### -- Create a Compute Engine Virtual Machine Instance
View a list of public images available on Compute Engine

```
gcloud compute images list
``` 

Make note of the name of the image of your choice, image family and the project containing the image

> Debian-10-buster-v20200902 - Image name.| debian-cloud - Project name

---
Create an Instance from a Public Image 

```
gcloud beta compute --project=qwiklabs-gcp-03-c8a0e4704dd2 instances create dev-instance \
--zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM \
--maintenance-policy=MIGRATE \
--service-account=1067373856093-compute@developer.gserviceaccount.com \
--scopes=https://www.googleapis.com/auth/cloud-platform --tags=http-server \
--image=debian-10-buster-v20200902 --image-project=debian-cloud \
--boot-disk-size=10GB --boot-disk-type=pd-standard \
--boot-disk-device-name=dev-instance --no-shielded-secure-boot \
--no-shielded-vtpm --no-shielded-integrity-monitoring \
--reservation-affinity=any
```

The command above creates an instance with the following characteristics
> Instance name: dev-instance
Zone: us-central1-a
Machine type: e2-medium
Subnet: default
Network: Premium
Maintenance Policy: Migrate
Service Account: 1067373856093-compute@developer.gserviceaccount.com
Tags: http-server
Image: debian-buster-v20200902
Image Project: debian-cloud
Boot Disk Size: 10GB
Boot Disk Type: pd-standard

---
Configure firewall for this instance


```
gcloud compute --project=qwiklabs-gcp-03-c8a0e4704dd2 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
```

The above command enables firewall rule and allows http full access to all cloud APIs

---
### -- Install Software on the VM Instances
From the **Google Console** > **Compute Engine** >> **VM Instance**, on the instance created, enter **SSH** using the SSH button and execute the following commands

```
sudo apt-get update
```

Then install git with this command

```
sudo apt-get install git
```
If prompted, press Enter
	
---
To download the nodejs script, execute this command

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
```

---
To install npm and Nodejs, execute the following command

```
sudo apt install nodejs
```


---
### -- Configure the VM to Run Application Software
To check the version of your node, execute this

```
node -v
```

---
To clone the class repository, do

```
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```

---
To change the working directory, execute

```
cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/
```

---
To run a simple web server, execute the following command

```
sudo node server/app.js
```

---
To view the app, execute this command to get the external IP address

```
gcloud compute instances describe dev-instance \
 --format='get(networkInterfaces[0].accessConfigs[0].natIP)'
```

Copy the external IP and paste in a new browser window to view the app

---
Return to the SSH window and stop the application by typing ctrl + C 

---
To install the Node.js library for Compute Engine, execute the following command:

```
sudo apt install npm
```

---
To run a simple Node.js application that lists Compute Engine instances, execute the following command:

```
node list-gce-instances.js
```