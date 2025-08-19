# Devops-maven-simple-project

# Tools Install
https://github.com/HVAksh/tools-Installation-for-devops-projects.git


# Jenkins Configuration
Install jenkins with default plugins and install other plugins
    - eclipse temurin installer
    - docker, docker commons, Docker pipeline, Docekr API, need to check if docker-build-step is mandatory or not.

# Configure tools:
use auto install or as per your knowledge, If not installed on JENKINS Server (Java is a prerequisite of Jenkins)
    - maven/nodejs or both as per project
    - JDK
    - docker

# Docker configure
    - go to dockerhub, account settings, security
    - Create PAT with read write and delete access
    - copy token and go to jenkins

# Config on Jenkins for Docker-CREDS:
    - go to admin-security users token and generate token with name
    - copy and save on local for time being
    - go to manage jenkins, Security -- Creds, secret text, give any id and token add

# Job Creation
#                                                                             **NOTE**
#                                                    Complete this in 2 stages to understand and learn
#               Stage1- Only create pipeline(cleanWS, Checkout, mvn Build), only mvn is mentioned in tools, no other major config till here.
#               Stage2- Create Pipeline for Docker build and push. 
    - Go to Jenkins, New Item,
    - Create Pipeline type of Project so that you can take help from PIPELINE systax.
    - Go to Pipeline Section and Select- Pipeline Script from SCM (if you are using JENKINSFILE as in this project)
    OR
    - If you are new use Pipeline script and create script here only.
    - Make sure Repo is Public since we are not using any creds this time.
    - Change branch to main
    - Script Path should match the jenkinsfile name in Repository. SAVE and APPLY

#    Build Now, in case not successfull click on build number and check CONSOLE output to troubleshoot.