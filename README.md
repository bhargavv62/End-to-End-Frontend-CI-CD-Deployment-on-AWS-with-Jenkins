## End-to-End-Frontend-CI-CD-Deployment-on-AWS-with-Jenkins
# Description

In modern software development, Continuous Integration (CI) and Continuous Deployment (CD) have become vital for delivering applications faster and with greater consistency.
This project demonstrates how to automate the deployment of a Java web application on an Apache Tomcat server using a Jenkins-based CI/CD pipeline.
By integrating Git for source control and Maven for build automation, the process ensures a smooth, reliable, and repeatable deployment cycle from code commit to production release.

# Tools Overview

1) Git – A distributed version control system that manages source code efficiently and enables seamless collaboration among developers.

2) Maven – A build and dependency management tool that simplifies compiling, packaging, and maintaining Java projects.

3) Jenkins – The automation server that powers the CI/CD pipeline, handling code integration, testing, and deployment with minimal manual effort.

4) Apache Tomcat – A dependable, open-source application server used to host and run Java-based web applications in various environments.

# Real-World Scenario

Imagine a development team working on an e-commerce web application. Whenever a developer updates the product catalog, the changes are pushed to GitHub, automatically triggering the CI/CD pipeline.

Here’s the automated workflow in action:

1) Jenkins fetches the latest code from the GitHub repository.

2) Maven compiles the application and executes unit tests to ensure code quality and stability.

3) Upon successful testing, Jenkins deploys the newly built version to the Apache Tomcat server.

This end-to-end automation removes manual steps, minimizes deployment time, and guarantees that the application remains current, reliable, and production-ready.

## Step by step  Deployment of End-to-End-Frontend-Application-on-AWS-with-Jenkins

# STEP-1: Launch Two EC2 Instances 

Jenkins Server

Tomcat Server

<img width="2386" height="426" alt="image" src="https://github.com/user-attachments/assets/cc44c903-f2b5-4223-8ad0-f4bbaf109627" />


# STEP-2: Connect Jenkins server and setting up Jenkins & GIT
- <a href="https://github.com/bhargavv62/End-to-End-Frontend-CI-CD-Deployment-on-AWS-with-Jenkins/blob/main/Setting%20Up%20Git%20and%20Jenkins.html">setting up git & jenkins</a>

Now copy the public-ip of your system and access it with 8080 port.


![web](https://github.com/user-attachments/assets/97c8a9ce-fb80-4356-a4a6-a0fd1be16fa7)

# STEP-3: Add the Deploy to Container plugin in Jenkins

Go to Manage Jenkins » Plugins » Available Plugins » Deploy to container

<img width="2880" height="764" alt="image" src="https://github.com/user-attachments/assets/dd848c8e-7c27-492b-8c27-89ac098f76bd" />

# STEP-4: Connect Maven to the Build Pipeline

Go to Manage Jenkins » tools and select maven

under the Maven Installations click on Add Maven

Name: mymaven

Version: default (3.9.9)


<img width="2846" height="1542" alt="image" src="https://github.com/user-attachments/assets/29126666-f19c-460d-91d9-111fb375bd70" />
Now click on save

# STEP-5: Define a Freestyle Job in Jenkins

<img width="2878" height="1574" alt="image" src="https://github.com/user-attachments/assets/f8ec739b-f839-4e7f-ad95-eca6a9e48a1c" />
Go to Source Code Management and select Git and enter the repo-url (https://github.com/usubbu/one.git)


<img width="2880" height="1382" alt="image" src="https://github.com/user-attachments/assets/abb0c1ff-d39f-4457-b984-6c815b9ffcd3" />

Go to Build Steps and select Invoke top-level Maven targets and select the Maven version as mymaven

Now enter the goal as clean package


<img width="2874" height="1566" alt="image" src="https://github.com/user-attachments/assets/be7d351e-59fe-4501-92ad-7f72466b7204" />

Save the job and click on Build Now


<img width="1302" height="1094" alt="image" src="https://github.com/user-attachments/assets/5c2a28a0-44b9-4e86-ae74-8e00fa9b1063" />
If the build gets success, go to workspace and open the target folder, we will get war file


<img width="1898" height="1140" alt="image" src="https://github.com/user-attachments/assets/a5d3fa60-4116-444a-9663-91f13698e2b9" />

# STEP-6: Deploy the application on Tomcat Server

connect the tomcat server and run the script to setup tomcat

Run the below script to setup tomcat

- <a href="https://github.com/bhargavv62/End-to-End-Frontend-CI-CD-Deployment-on-AWS-with-Jenkins/blob/main/tomcat%20setup.html">Tomcat setup</a>

Remember the tomcat credentials
•	username**:** tomcat
•	password**:** admin@123
If you would like to modify, change the credentials on above script also.
Now access the tomcat dashboard with public-ip of tomcat server with 8080 port.

<img width="2852" height="1300" alt="image" src="https://github.com/user-attachments/assets/9e3bf9e6-3935-4d3b-955b-f2a43a6b1f4c" />
Now go to Manager App and enter the credentials, You will get the Tomcat Web Application Manager dashboard.
<img width="2880" height="1460" alt="image" src="https://github.com/user-attachments/assets/0c0fa523-7363-4456-835f-798d18932f7b" />

# STEP-7: Integrate Tomcat with Jenkins

Configure the Jenkins job and select Post Build Actions and select Deploy war/ear to a container

WAR/EAR file: target/*.war

context path: swiggy

<img width="2876" height="1568" alt="image" src="https://github.com/user-attachments/assets/6d1163d2-4495-4494-a121-5fd6fa148e6f" />

and click on add container and select Tomcat 9.x Remote

<img width="2860" height="1534" alt="image" src="https://github.com/user-attachments/assets/0e1f4a8f-9c6e-4f7f-9649-8ca0602b0a70" />
Now add the tomcat credentials, click on Add select Jenkins

<img width="2256" height="1430" alt="image" src="https://github.com/user-attachments/assets/be052c13-6ae2-4ff8-b67d-8241204562d1" />

Now click on Add and select the credentials and enter the tomcat url

<img width="2724" height="1550" alt="image" src="https://github.com/user-attachments/assets/09c3146e-7d58-4c81-b1b9-d962ad8ff0c8" />

Now save the job and click on Build Now, If the build gets success then our application will be deployed on tomcat successfully.

<img width="1594" height="1352" alt="image" src="https://github.com/user-attachments/assets/4992d8f3-600a-4a74-a7b3-49ddac7f5c6b" />

The build is success, Now lets refresh the tomcat page and we will see swiggy app is running


<img width="2870" height="1492" alt="image" src="https://github.com/user-attachments/assets/9a8ca7e3-1d3e-45b5-b4fd-e178cbea48ac" />

Open the swiggy app and check the output.

We can also implement Webhooks to automate the delivery process.

# Best Practices

1) Use a staging environment to test and validate deployments before releasing them to production.

2) Incorporate automated testing within your CI/CD pipeline to detect and fix issues early in the development cycle.

3) Secure Jenkins and Tomcat by enforcing authentication, managing access permissions, and performing regular updates.


# Conclusion

Implementing CI/CD automation accelerates software delivery, reduces manual errors, and improves overall consistency.

Deploying Java applications to Apache Tomcat with Jenkins and Maven becomes effortless with a well-structured pipeline.

By embracing CI/CD, teams can deliver reliable releases faster while dedicating more time to innovation and continuous improvement.


# 👨‍💻 Author & Contributors
Bhargav 💡 maintains this project.Open to feedback, ideas, and contributions are warmly welcomed.

# 🤝 Let’s Collaborate:

GitHub: https://github.com/bhargavv62

LinkedIn: https://linkedin.com/in/

# ⭐ Support the Project
If you found this project helpful, please consider:


•	Starring ⭐ the repository

•	Sharing it with your network

•	Contributing to its improvement

