# jenkins-installation-ubuntu
A step-by-step guide to installing Jenkins on an Ubuntu server. This documentation covers the process from setting up Java to accessing and unlocking the Jenkins web interface.

# Step 1: Update Package Lists
First, it's always good practice to update the package lists to ensure you have the latest information about available packages. Open your terminal and run:


*****************

sudo apt update
*****************

# Step 2: Install Java
Jenkins requires Java to run. Install OpenJDK, an open-source implementation of the Java Platform:



*******************************************

sudo apt install openjdk-11-jre-headless
*******************************************

To verify the Java installation:

*************
java -version
************* 
#  Step 3: Add Jenkins Repository and Install Jenkins

Import the Jenkins repository GPG key:

**************************************************************** 

wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
***************************************************************** 

Add the Jenkins repository to the system's APT sources:
*****************************************************************  

sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
***************************************************************** 

Update the package lists again:
************************************************************

sudo apt update
************************************************************
#  Install Jenkins:
************************************************************

sudo apt install jenkins
************************************************************
#  Step 4: Manage Jenkins Service

After the installation, Jenkins should start automatically. Check its status:

************************************************************

sudo systemctl status jenkins
************************************************************
If, for some reason, Jenkins isn't running, you can start it:

************************************************************

sudo systemctl start jenkins
************************************************************
For enabling Jenkins to start at boot:

************************************************************

sudo systemctl enable jenkins

************************************************************
#  Step 5: Access Jenkins Web Interface

Jenkins listens on port 8080 by default. In your web browser, navigate to:

************************************************************

http://your_server_ip_or_hostname:8080
************************************************************
#  Step 6: Unlock Jenkins

For first-time access, you'll need to unlock Jenkins. Fetch the initial admin password:

************************************************************

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
************************************************************
Use this password in the Jenkins web interface to proceed.

#  Step 7: Complete Jenkins Setup

Follow the Jenkins web interface's prompts. This includes:

Installing recommended plugins.
Configuring an admin user.
With the setup complete, Jenkins is ready for use. Dive into creating projects, managing builds, and setting up CI/CD pipelines
