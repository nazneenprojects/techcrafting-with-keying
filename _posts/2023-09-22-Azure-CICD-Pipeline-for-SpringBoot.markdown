# How to set up Azure-CICD-pipeline for SpringBoot Project

Prerequisites : 
 - Microsoft Azure DevOps credentials
 - SpringBoot project with maven build
 - any VM or local machine (linux used here for thsi demo)

Steps :
  1.  Go to your DevOps Organization -> agent pool -> create new agent based on your VM or local machine OS
  2.  Configure and run it using ./config.sh and ./run.sh
  3.  Once agent starts, you will see running status in your agent pool -> agent section
  4.  Create Project for CICD pipleline under your organization
  5.  Now its time to connect code repository . If you are using Github, bitbucket etc Azure give you proviion to link your account in DevOps platform. Go to pipeline section -> Repository -> click on Github -> Authentiacte and select repository.
  6.  On Github , you can create simple SpringBoot project with maven support and add azure-pipeline.yaml file to execute the CICD pipeline
  7.  
