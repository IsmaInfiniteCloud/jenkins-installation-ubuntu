# jenkins-installation-ubuntu
A step-by-step guide to installing Jenkins on an Ubuntu server. This documentation covers the process from setting up Java to accessing and unlocking the Jenkins web interface.


Jenkins Installation Guide for Ubuntu
A step-by-step guide to installing Jenkins on an Ubuntu server. This documentation covers the process from setting up Java to accessing and unlocking the Jenkins web interface.

Step 1: Update Package Lists
First, it's always good practice to update the package lists to ensure you have the latest information about available packages. Open your terminal and run:



(sudo apt update)
Step 2: Install Java
Jenkins requires Java to run. Install OpenJDK, an open-source implementation of the Java Platform:




(sudo apt install openjdk-11-jre-headless)
Verify the Java installation with:




java -version
Step 3: Add Jenkins Repository and Install Jenkins
To get the latest stable release, add the Jenkins repository and install Jenkins:

Add the Jenkins repository key to apt:



wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
Add the Jenkins repository to apt sources:



sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
Update package lists:



sudo apt update
Install Jenkins:
 
sudo apt install jenkins
Step 4: Start Jenkins Service
After Jenkins installation, it should start automatically. To check its status, run:

 
sudo systemctl status jenkins
If Jenkins isn't running, start it with:

bash
Copy code
sudo systemctl start jenkins
Step 5: Access Jenkins Web Interface
By default, Jenkins runs on port 8080. Access the Jenkins web interface by entering your server's IP address or hostname followed by :8080 in your web browser:

 
http://your_server_ip_or_hostname:8080
Step 6: Unlock Jenkins
The first time you visit the Jenkins web interface, you'll need to unlock Jenkins. Retrieve the initial admin password using:

 
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Copy this password and paste it into the web interface to unlock Jenkins.

Step 7: Complete Jenkins Setup
Follow the on-screen instructions in the Jenkins web interface to complete the setup, including installing suggested plugins and setting up an admin user.

Once set up is complete, Jenkins will be ready for use. You can then begin creating Jenkins jobs and managing CI/CD workflows.
