# Deploying Spring Boot App using K8s, ArgoCD, Jenkins and all

Successfully deploy a Spring Boot application using a robust CI/CD pipeline. It provides an overview of the technologies and processes involved, including Jenkins, SonarQube, Kubernetes, ArgoCD, and Microsoft Azure.

<!--video uploading here-->

## 🎥 Watch the tutorial video [here](https://player.vimeo.com/video/948914848).

# Workflow Diagram-
![jenkins workflow](https://github.com/user-attachments/assets/3b04a34b-3c0e-4ad5-87fc-ae7d12d79b61)


## Project Overview

This project demonstrates the deployment of a Spring Boot application using a fully automated DevOps pipeline. The key components and technologies used in this project are:

- **Spring Boot**: A Java-based framework used to create stand-alone, production-grade Spring applications.
- **Maven:** A build automation tool used primarily for Java projects.
- **Jenkins**: An open-source automation server used to build, test, and deploy our application.
- **SonarQube**: A tool for continuous inspection of code quality to perform automatic reviews.
- **Kubernetes:** An open-source platform for automating the deployment, scaling, and management of containerized applications.
- **ArgoCD**: A declarative, GitOps continuous delivery tool for Kubernetes.
- **Microsoft Azure:** A cloud computing service used for deploying and managing applications.

# Getting Started
## Prerequisites
Before setting up this project, ensure you have the following prerequisites:

- **Microsoft Azure Account**: You will need an Azure account to provision a Resource Group and create a Virtual Machine in the RG. If you don't have an Azure account you can [create one here](https://signup.live.com/signup?sru=https%3a%2f%2flogin.live.com%2foauth20_authorize.srf%3flc%3d1033%26client_id%3d51483342-085c-4d86-bf88-cf50c7252078%26cobrandid%3d788a943c-8e34-4c0a-9c83-1e4ef0322879%26mkt%3dEN-US%26opid%3d32AE1738B573F897%26opidt%3d1715941888%26uaid%3d35fcf7c10d4343389192c4200722161b%26contextid%3d741CCF2D50723A8F%26opignore%3d1&mkt=EN-US&uiflavor=web&lw=1&fl=easi2&cobrandid=788a943c-8e34-4c0a-9c83-1e4ef0322879&client_id=51483342-085c-4d86-bf88-cf50c7252078&uaid=35fcf7c10d4343389192c4200722161b&suc=8e0e8db5-b713-4e91-98e6-470fed0aa4c2&lic=1).

    - Launch a virtual machine with the Ubuntu 22.04 LTS image and choose the size D2ads v5 - 2 vCPUs and 8 GiB memory because we need to access more things like Jenkins, SonarQube, Kubernetes, ArgoCD, and much more.

   - **SSH Access**: Connect to your Azure VM using SSH or any preferred method for configuration and setup.

---

Now install Jenkins-
```bash
#!/bin/bash
sudo apt update -y
wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | sudo tee /etc/apt/keyrings/adoptium.asc
echo "deb [signed-by=/etc/apt/keyrings/adoptium.asc] https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list
sudo apt update -y
sudo apt install temurin-17-jdk -y
/usr/bin/java --version
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
sudo systemctl start jenkins
sudo systemctl status jenkins
```

After running this script, use your `<VM-publicIP:8080>` and access it via the browser.

- after that install docker using these command-
   ```bash
   sudo apt install
   ```

   ```bash
   sudo apt update -y
   ```

   ```bash
   sudo apt install docker.io -y
   ```

- Docker group for permissions.

   ```bash
   sudo usermod -a -G docker $USER
   ```

- Switch primary group to Docker for current session.

   ```bash
   newgrp docker
   ```

- Granting universal read, write, and execute permissions to Docker socket.

    ```bash
    sudo chmod 777 /var/run/docker.sock
    ```

- now install sonarqube using this-
    ```bash
    docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
    ```
   After run the container Use your <VM-publicIP:9000> for sonarqube dashboard and access it via the browser. and enter username `admin` & password is also `admin`.
  


- after all then Install plugins on Jenkins-
- Plugins Prerequisites in Jenkins-

    1. `Pipeline`
    2. `Docker API Plugin`
    3. `Docker Pipeline`
    4. `SonarQube Scanner`
    5. `Maven Integration`
    6. `Blue Ocean`
    7. `Git`

 - Now, in Jenkins credentials, add the credentials for `Docker`, `Github`, and `Sonarqube`. and after done of it's then run the Pipeline Script.
   - This result appears as shown in the following screenshot-
     <br/>
     <br/>
     
     ![pipeline Screenshot](https://github.com/mdazfar2/maven-jenkins-ArgoCD/assets/100375390/04517050-4b7d-4267-90c3-efe3cc0a17d4)


- Now install the Kubeadm because we are deploy ArgoCD using Kubernetes cluster, Visit the installation of [kubernetes](https://github.com/mdazfar2/ShellScript-Toolkit/tree/main/kubernetes%20Installation).
  
- you can also use kubernetes using Azure Kubernetes Service (AKS).
  <br/>
  
- for deploy argoCD visit the [argocd documentation](https://github.com/mdazfar2/ShellScript-Toolkit/tree/main/ArgoCD%20Installation).

- after done of it's upload your github project link in `New App`.
- And hope you can understand by the above tutorial video.

# Conclusion

This project demonstrates a robust DevOps pipeline using Jenkins, SonarQube, Docker, Kubernetes, ArgoCD, and Azure. It ensures continuous integration and delivery, code quality, and automated deployment, providing a scalable and resilient environment for the Spring Boot application.


<img src="https://www.animatedimages.org/data/media/562/animated-line-image-0184.gif" width="1920" />

***That’s all from my side. If you encounter any issues while working on this project, feel free to connect with me via-***

- [LinkedIN](https://www.linkedin.com/in/sa-chin/)
- [Discord](https://discord.com/channels/@me)
- [Mail Me](mailto:sachin.profess@gmail.com)

**Your insights are valuable and will help improve this project for everyone. Don't hesitate to connect!** ✨😊
