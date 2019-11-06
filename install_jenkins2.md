# Install Jenkins 2.x in Ubuntu 18.04

1. Update the package list and upgrade if necessary.
     ```shell script
     sudo apt update
     sudo apt upgrade -y
     ```
1. Install Java 8 OpenJDK.
    ```shell script
    sudo apt install openjdk-8-jdk
    ```
1. Import the GPG Keys of the Jenkins repository. You should see an 'OK' message if successful.
    ```shell script
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   ```
1. Add the Jenkins repository in the system.
    ```shell script
    sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    ```
1. Install Jenkins.
    ```shell script
    sudo apt install jenkins
    ```
1. Check if Jenkins is running.
    ```shell script
    systemctl status jenkins
    ```
