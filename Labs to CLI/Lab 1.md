# GCP Command Line Interface (CLI) codes

### Lab 1 - GCP Fundamentals: Getting Started with App Engine

### --Initialize App Engine
---
Initialize app engine app with my project and choose its region
`gcloud app create --project=$DEVSHELL_PROJECT_ID`

*When prompted for region selection, select region of choice where App Engine application will be located*

---
Clone the source code repository for a sample application in the hello_world directory
`git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

---
Navigate to the source directory
`cd python-docs-samples/appengine/standard_python3/hello_world`

---
---
### --Run Hello World Application locally
Execute the following command to download and update the packages list
`sudo apt-get update`

---
Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.
`sudo apt-get install virtualenv`

*If prompted, [Y/n], press Y and then Enter*

Next, execute the following command

`virtualenv -p python3 venv`

---
Activate the virtual environment

`source venv/bin/activate` 

---
Navigate to project directory and install dependencies
`pip install -r requirements.txt`

---
Run the application

`python main.py`

---
In the Cloud Shell, click **Web Preview** > **Preview on port 8080**  to preview the application

Return to Cloud Shell and press Ctrl + C to abort the deployed service

---
---
### -- Deploy and Run Hello World on App Engine
To deploy this application to the App Engine Standard environment
Navigate to the source directory
`cd ~/python-docs-samples/appengine/standard_python3/hello_world`

Deploy the Hello World application

`gcloud app deploy`

*Press Y, then Enter at prompt to continue* 

---
Launch browser to view the app at http://YOUR_PROJECT_ID.appspot.com
`gcloud app browse`

*Copy and paste the generated url into a new browser tab to view*

---
---
### -- Disable the application
Using command line tool, disable the application

`gcloud app versions stop v1`

**Disable through the console**

In the Cloud Console, on the navigation, click **App Engine** > **Settings**, then click **Disable application**. On the pop up box, enter the **App ID** and click **Disable**