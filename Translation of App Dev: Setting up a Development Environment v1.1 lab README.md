# GADS-Learning-Phase-2-Practice-Project
App Dev: Setting up a Development Environment v1.1
---------------------------------------------------------------
2 hours
Free
Rate Lab
----------------------------------------------------------------
Overview
In this lab, you will provision a Google Compute Engine virtual machine and install software libraries for Node.js software development on Google Cloud Platform.
----------------------------------------------------------------
Objectives
In this lab, you will learn how to perform the following tasks:

Provision a Google Compute Engine instance.

Connect to the instance using SSH.

Install software on the instance.

Verify the software installation.
-----------------------------------------------------------------
Setup

For each lab, you get a new GCP project and set of resources for a fixed time at no cost.

1.Make sure you signed into Qwiklabs using an incognito window.

2.Note the lab's access time  and make sure you can finish in that time block.

There is no pause feature. You can restart if needed, but you have to start at the beginning.

3.When ready, click Start Lab

4.Note your lab credentials. You will use them to sign in to Cloud Platform Console. 

5.Click Open Google Console.

6.Click Use another account and copy/paste credentials for this lab into the prompts.

  If you use other credentials, you'll get errors or incur charges.

7.Accept the terms and skip the recovery resource page.
  Do not click End Lab unless you are finished with the lab or want to restart it. This clears your work and removes the project.
-----------------------------------------------------------
Task 1: Creating a Compute Engine Virtual Machine Instance


1. In GCP console, on the top right toolbar, click the Open Cloud Shell button.

2.Click Continue.

3.To display a list of all the zones in the region to which Qwiklabs assigned you, enter this partial command gcloud compute zones list | grep followed by the region   that Qwiklabs or your instructor assigned you to.

  Your completed command will look like this:

	gcloud compute zones list | grep us-central1

4.Choose a zone from that list other than the zone to which Qwiklabs assigned you. For example, if Qwiklabs assigned you to region us-central1 and zone us-central1-a   you might choose zone us-central1-b.

5.To set your default zone to the one you just chose, enter this partial command gcloud config set compute/zone followed by the zone you chose.

  Your completed command will look like this:

	gcloud config set compute/zone us-central1-a

6.To create a VM instance called dev-instance in that zone, execute this command:

	gcloud compute instances create "dev-instance" \
	--machine-type "n1-standard-1" \
	--image-project "debian-cloud" \
	--image "debian-9-stretch-v20190213" \
	--subnet "default"

  Note: The VM can take about two minutes to launch and be fully available for use.

7.On the VM instances page, in the row for the dev-instance, click SSH (in the   Connect column).

  This launches a browser-hosted SSH session. If you have a popup blocker, you may need to click twice.

  There's no need to configure or manage SSH keys.

  Click Check my progress to verify the objective.
----------------------------------------------------------------------
Task 2: Install software on the VM instance

1.In the SSH session, to update the Debian package list, execute the following command:

	sudo apt-get update

2.To install Git, execute the following command:

	sudo apt-get install git

  If prompted, press Enter.

3.To download the Node.js setup script, execute the following command:

	curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

4.To install npm and Node.js, execute the following command:

	sudo apt install nodejs

  Click Check my progress to verify the objective.
  
----------------------------------------------------------------------
Task 3: Configure the VM to Run Application Software

  In this section, you will verify the software installation and run some sample codes.

1.To check the version of Node.js, execute the following command:

	node -v

  You should see the Node.js version number for version 6.

2.To clone the class repository, execute the following command:

	git clone https://github.com/GoogleCloudPlatform/training-data-analyst

  Click Check my progress to verify the objective.

3.To change the working directory, execute the following command:

	cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/

4.To run a simple web server, execute the following command:

	sudo node server/app.js

5.Return to the Cloud Console VM instances list, and click on the External IP address for the dev-instance.

  You should see a Hello GCP dev! message from Node.js.

6.Return to the SSH window, and stop the application by pressing Ctrl+C.

7.To install the Node.js library for Compute Engine, execute the following command:

	npm install

8.To run a simple Node.js application that lists Compute Engine instances, execute the following command:

	node list-gce-instances.js

  Many details about your machine should appear in the terminal window.

  Warning: If you try to do this on your own machine, it will not work if no credentials have been set up to access GCP on your machine.
--------------------------------------------------------------
End your lab
When you have completed your lab, click End Lab. Qwiklabs removes the resources you’ve used and cleans the account for you.

You will be given an opportunity to rate the lab experience. Select the applicable number of stars, type a comment, and then click Submit.

The number of stars indicates the following:

1 star = Very dissatisfied
2 stars = Dissatisfied
3 stars = Neutral
4 stars = Satisfied
5 stars = Very satisfied
You can close the dialog box if you don't want to provide feedback.

For feedback, suggestions, or corrections, please use the Support tab.

©Google, Inc. or its affiliates. All rights reserved. Do not distribute.

