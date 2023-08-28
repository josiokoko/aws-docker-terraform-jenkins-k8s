FROM jenkins/inbound-agent
LABEL mainter="Joseph Ayeni" 

USER root
# RUN apt update && apt install -y git curl unzip
RUN apt-get update && apt-get install -y lsb-release

RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
  
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli git curl unzip gettext-base

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip && ./aws/install

RUN curl -LO https://dl.k8s.io/release/v1.24.1/bin/linux/amd64/kubectl
RUN chmod +x kubectl

RUN mv kubectl /usr/local/bin/kubectl
ENTRYPOINT ["jenkins-slave"]