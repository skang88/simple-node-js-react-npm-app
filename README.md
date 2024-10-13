# simple-node-js-react-npm-app

This repository is for the
[Build a Node.js and React app with npm](https://jenkins.io/doc/tutorials/build-a-node-js-and-react-app-with-npm/)
tutorial in the [Jenkins User Documentation](https://jenkins.io/doc/).

The repository contains a simple Node.js and React application which generates
a web page with the content "Welcome to React" and is accompanied by a test to
check that the application renders satisfactorily.

The `jenkins` directory contains an example of the `Jenkinsfile` (i.e. Pipeline)
you'll be creating yourself during the tutorial and the `scripts` subdirectory
contains shell scripts with commands that are executed when Jenkins processes
the "Test" and "Deliver" stages of your Pipeline.


# Docker 설치

# 패키지 업데이트
sudo apt update

# Docker 설치를 위한 필수 패키지 설치
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

# Docker GPG 키 추가
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Docker 저장소 추가
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 패키지 목록 업데이트 후 Docker 설치
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y

# Docker 서비스 실행 및 부팅 시 자동 실행 설정
sudo systemctl enable docker
sudo systemctl start docker



# Docker compose 설치
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Jenkins Docker 컨테이너 실행
sudo docker run -d -p 8080:8080 -p 50000:50000 --name jenkins --restart=unless-stopped -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts

# 초기설정
sudo docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

