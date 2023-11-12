FROM jenkins/jenkins:2.414.3-jdk17
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
# Download and extract Apache Maven - Lab8
RUN curl http://mirrors.estointernet.in/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz --output /var/jenkins_home/apache-maven-3.6.3-bin.tar.gz
RUN tar -xvzf /var/jenkins_home/apache-maven-3.6.3-bin.tar.gz -C /var/jenkins_home
RUN rm /var/jenkins_home/apache-maven-3.6.3-bin.tar.gz
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"