# How to set up Azure CICD Pipeline for SpringBoot Project

Prerequisites : 
 - Microsoft Azure DevOps credentials
 - SpringBoot project with maven build
 - any VM or local machine (linux used here for thsi demo)

Steps :
  1.  Go to your DevOps Organization -> agent pool -> create new agent based on your VM or local machine OS
     ![Screenshot from 2024-02-20 19-13-27](https://github.com/nazneenprojects/techcrafting-with-keying/assets/50543241/1224ded8-8c6f-4dfe-8c5f-b100b7848590)
     ![Screenshot from 2024-02-20 19-13-02](https://github.com/nazneenprojects/techcrafting-with-keying/assets/50543241/1c2e6216-dcc4-43ac-9845-9ea075db5972)

  2.  Configure and run it using ./config.sh and ./run.sh
     
  

```
admin@admin:/myagent$ cd ..
admin@admin:/$ sudo chmod o+w /myagent
admin@admin:/$ cd myagent/
admin@admin:/myagent$ ./config.sh 

  ___                      ______ _            _ _
 / _ \                     | ___ (_)          | (_)
/ /_\ \_____   _ _ __ ___  | |_/ /_ _ __   ___| |_ _ __   ___  ___
|  _  |_  / | | | '__/ _ \ |  __/| | '_ \ / _ \ | | '_ \ / _ \/ __|
| | | |/ /| |_| | | |  __/ | |   | | |_) |  __/ | | | | |  __/\__ \
\_| |_/___|\__,_|_|  \___| \_|   |_| .__/ \___|_|_|_| |_|\___||___/
                                   | |
        agent v3.234.0             |_|          (commit 21ca259)


>> End User License Agreements:

Building sources from a TFVC repository requires accepting the Team Explorer Everywhere End User License Agreement. This step is not required for building sources from Git repositories.

A copy of the Team Explorer Everywhere license agreement can be found at:
  /myagent/license.html

Enter (Y/N) Accept the Team Explorer Everywhere license agreement now? (press enter for N) > 

>> Connect:

Enter server URL > https://dev.azure.com/naz18mulani/
Enter authentication type (press enter for PAT) > PAT
Enter personal access token > ****************************************************
Connecting to server ...

>> Register Agent:

Enter agent pool (press enter for default) > 
Enter agent name (press enter for admin) > zermatt
Scanning for tool capabilities.
Connecting to the server.
Successfully added the agent
Testing agent connection.
Enter work folder (press enter for _work) > 
2024-02-20 17:05:45Z: Settings Saved.
admin@admin:/myagent$ ./run.sh
Scanning for tool capabilities.
Connecting to the server.
2024-02-20 17:06:50Z: Listening for Jobs
Error reported in diagnostic logs. Please examine the log for more details.
    - /myagent/_diag/Agent_20240220-170644-utc.log
2024-02-20 17:59:09Z: Agent connect error: The HTTP request timed out after 00:01:00.. Retrying until reconnected.
2024-02-20 18:00:45Z: Agent reconnected. 
```
  ![Screenshot from 2024-02-20 19-26-46](https://github.com/nazneenprojects/techcrafting-with-keying/assets/50543241/c1f2891d-0f82-4b5f-a9cb-6c0854994055)

 
  3.  Once agent starts, you will see running status in your agent pool -> agent section
  4.  Create Project for CICD pipleline under your organization
  5.  Now its time to connect code repository . If you are using Github, bitbucket etc Azure give you proviion to link your account in DevOps platform. Go to pipeline section -> Repository -> click on Github -> Authentiacte and select repository.
  6.  On Github , you can create simple SpringBoot project with maven support and add azure-pipeline.yaml file to execute the CICD pipeline
    
