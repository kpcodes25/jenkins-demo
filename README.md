# jenkins-demo

# Jenkins CI/CD Setup (Beginner Friendly) -- manual

This repository documents how to install Jenkins on Windows
and create a simple CI pipeline using GitHub.

---

## 🧩 Prerequisites
- Windows Laptop
- GitHub Account
- Internet Connection

---

## 🔹 Step 1: Install Java (Required)

1. Download Java 17 from:
   https://adoptium.net
2. Install Java (keep default options)
3. Verify installation:
   ```cmd
   java -version

-------------------------------------------
Download Jenkins:
https://www.jenkins.io/download/

Download Jenkins.msi

Install with default settings

Choose:

Run service as LocalSystem

Jenkins installs as Windows Service

-------------------------------------------------
Change Jenkins Port:

Stop Jenkins service

Edit file:

C:\Program Files\Jenkins\jenkins.xml


Change:

--httpPort=8080


to:

--httpPort=8081


Start Jenkins service

-------------------------------------

Step 4: Unlock Jenkins

Open:

http://localhost:8081


Copy password from:

C:\Program Files\Jenkins\secrets\initialAdminPassword

----------------------------------------

Step 5: Create Jenkins Pipeline

Open Jenkins Dashboard

Click New Item

Select Pipeline

Name: jenkins-demo-pipeline

----------------------------------------

Step 6: Jenkinsfile

Create a file named Jenkinsfile in this repository:

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub'
            }
        }

        stage('Build') {
            steps {
                echo 'This is a simple CI pipeline'
            }
        }
    }
}

-----------------------------------------------------------------

Step 7: Configure Jenkins Pipeline

Definition: Pipeline script from SCM

SCM: Git

Repository URL:

https://github.com/<your-username>/jenkins-demo.git


Branch:

*/main

--------------------------------------------------

Step 8: Run Build

Click Build Now

Check Console Output

Verify successful build

✅ Result

Jenkins installed on Windows

GitHub integrated

CI pipeline executed successfully

------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

Jenkins CI Pipeline with GitHub Webhook & Gradle

Tech Stack

Jenkins – CI server

GitHub – Source code management

Gradle (Gradle Wrapper) – Build automation

ngrok – Expose local Jenkins to GitHub Webhooks

Windows OS

------------------------
CI Workflow

Developer pushes code to the GitHub repository

GitHub Webhook sends a POST request to Jenkins

Jenkins detects the change and starts the pipeline

Jenkins pulls the latest code

Build runs using Gradle Wrapper (gradlew)

Build status is displayed in Jenkins

--------------------------------------------

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Gradle') {
            steps {
                bat 'gradlew clean build'
            }
        }
    }
}
--------------------

> start jenkins
http://localhost:8081


> Start ngrok

> for the first time the authenticated token need to be added 

ngrok config add-authtoken 2xYpABCDEF1234567890

ngrok http 8081


--------------------------
GitHub Webhook Configuration
Payload URL
https://<ngrok-url>/github-webhook/

Content type: application/json

Events: Push events

ngrok is used to expose the locally running Jenkins instance to GitHub.

   
