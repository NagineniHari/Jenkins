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
SonarQube Scanner
AnsiColor

## Credentials
ssh-creds
aws-creds
sonar-token
github-token

## Master Agent Architecture
Create credentials to connect agent
Install Java in agent
Select Non verification strategy

## Trivy Installing
curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sudo sh -s -- -b /usr/local/bin v0.68.2

## image scaning command

trivy image \
  --severity HIGH,CRITICAL,MEDIUM \
  --exit-code 1 \
  --no-progress \
  --format table \
  --pkg-types os \
  996058207546.dkr.ecr.us-east-1.amazonaws.com/safety/catalogue:1.1.0