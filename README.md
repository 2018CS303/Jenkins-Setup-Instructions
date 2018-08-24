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

- Before starting Jenkins, let us change the default *$JENKINS_HOME* directory.

  - First create a directoy named *Jenkins* at any location you prefer. For this example, I will create it in my home folder `/home/rajula/Jenkins`. (To create a folder use `mkdir /home/rajula/Jenkins`)
  - Modify the contents of the file `/etc/default/jenkins`. Change the parameter of *$JENKINS_HOME* to the newly created folder path

- Jenkins is now installed as a daemon service. To start Jenkins run the command

  `systemctl start jenkins`

- To stop Jenkins run the command

  `systemctl stop jenkins`

# Using Jenkins

- Once Jenkins is running, navigate to `http://localhost:8080` in your browser
