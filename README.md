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



