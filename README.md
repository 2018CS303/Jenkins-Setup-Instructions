# Jenkins - Lab Session - 24/08/2018

### What is Jenkins?

- [Jenkins](http://jenkins.io/) is an _Open Source_ automation server
- It is one of the most popular continous integration (CI) server 
- It is written in Java
- It automatically builds, tests & deploys software

### What is it used for?

- Run tests & builds
- Trigger jobs automatically
- Automate deployments
- Get alerts when there is a failure
- Improves developers workflow

### Important terminologies in Jenkins

- Master
  - The central, coordinating process which stores configuration, loads plugins, and renders the various user interfaces for Jenkins.
- Node
  - A machine which is part of the Jenkins environment and capable of executing Pipelines or Projects. Both the Master and Agents are considered to be Nodes.
- Project
  - A user-configured description of work which Jenkins should perform, such as building a piece of software, etc
- Build
  - Result of a single execution of a Project
- Step
  - A single task; fundamentally steps tell Jenkins what to do inside of a Pipeline or Project
- Artifact
  - An immutable file generated during a Build or Pipeline run which is archived onto the Jenkins Master for later retrieval by users
- Pipeline
  - A user-defined model integrating different steps
- Plugin
  - An extension to Jenkins functionality provided separately from Jenkins Core
- Item
  - An entity in the web UI corresponding to either a: Folder, Pipeline, or Project
- Workspaces
  - A disposable directory on the file system of a Node where work can be done by a Pipeline or Project. Workspaces are typically left in place after a Build or Pipeline run completes unless specific Workspace cleanup policies have been put in place on the Jenkins Master.

More terminologies can be found [here](https://jenkins.io/doc/book/glossary/#project)

# Installation steps

### Pre-requisities

#### Java 8

- Make sure Java is installed on your machine. Verify it by running `java -version`. The output should be somewhat similar to

  ```sh
  openjdk version "1.8.0_181"
  OpenJDK Runtime Environment (build 1.8.0_181-8u181-b13-0ubuntu0.16.04.1-b13)
  OpenJDK 64-Bit Server VM (build 25.181-b13, mixed mode)
  ```
- If not, install it by running the commands

  ```sh
  sudo add-apt-repository ppa:openjdk-r/ppa
  sudo apt update
  sudo apt -y install openjdk-8-jdk
  ```
  - In case you have multiple java versions and want to set Java 8 as default, then run the command

    ```sh
    sudo update-alternatives --config java
    ```

### Installing Jenkins

- To install Jenkins, run the following commands

  ```sh
  wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
  sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
  sudo apt update
  sudo apt -y install jenkins
  ```

  ### Starting Jenkins

- Before starting Jenkins, let us change the default **$JENKINS_HOME** directory.

  - First create a directoy named **Jenkins** at any location you prefer. For this example, I will create it in my home folder `/home/rajula/Jenkins`. (To create a folder use `mkdir /home/rajula/Jenkins`). The path `/home/rajula/Jenkins` needs to be changed to an appropriate path w.r.t your system
  - Since, Jenkins runs the service as a *jenkins* user, we need to give write permissions to *jenkins* user for the newly created directoy. To do so, run the comand `sudo chmod 777 -R /home/rajula/Jenkins`
  - Modify the contents of the file `/etc/default/jenkins`. Change the parameter of **$JENKINS_HOME** to the newly created folder path. As it is in `/etc/` directory, you need to sudo permissions to edit the file. You can edit the file using any editor such as vim, gedit, nano etc. To edit it run the command `sudo gedit /etc/default/jenkins`

- Jenkins is now installed as a daemon service. To start Jenkins run the command

  `sudo systemctl start jenkins`

- To stop Jenkins run the command

  `sudo systemctl stop jenkins`

  Make sure to stop Jenkins using the above command, when you are not using it

- In case, you need to restart Jenkins at any point of time, run the command
`sudo systemctl restart jenkins`

  # Using Jenkins

- Once Jenkins is up and running, navigate to `http://localhost:8080` in your browser & follow the instructions

# References

- https://jenkins.io/ 
- https://jenkins.io/doc/book/installing/#debianubuntu
- https://github.com/cirulls/hands-on-jenkins
- https://jenkins.io/doc/book/glossary/#project
