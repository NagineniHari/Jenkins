## Jenkins Setup

# Partition the disk
sudo growpart /dev/xvda 4

sudo lvextend -L +10G /dev/mapper/RootVG-varVol
sudo lvextend -L +10G /dev/mapper/RootVG-rootVol
sudo lvextend -l +100%FREE /dev/mapper/RootVG-homeVol

sudo xfs_growfs /
sudo xfs_growfs /var
sudo xfs_growfs /home

## Installation commands for Jenkins from official doc
sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

# Add required dependencies for the jenkins package
sudo yum install fontconfig java-21-openjdk -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl enable jenkins
sudo systemctl start jenkins

## For Agent only java installation
sudo yum install fontconfig java-21-openjdk -y

## Managed Plugins
Stage view
Pipeline Utility Steps
AWS Credentials
AWS Steps


## Master Agent Architecture
Create credentials to connect agent
Install Java in agent
Select Non verification strategy