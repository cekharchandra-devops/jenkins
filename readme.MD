# Jenkins Installation

```
sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-17-openjdk -y
sudo yum install jenkins -y
# sudo systemctl daemon-reload
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

**Continous Integration**
***Continuous Integration (CI) is a software development practice where developers frequently merge their code changes into a shared repository. After each merge, the code is automatically built and tested to catch errors early. ***

Jenkins Plugins:

pipeline stage view