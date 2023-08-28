FROM jenkins/inbound-agent
LABEL mainter="Joseph Ayeni" 

USER root
RUN apt update && apt install -y git curl unzip
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-aarch64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip && ./aws/install

RUN curl -LO https://dl.k8s.io/release/v1.24.1/bin/linux/amd64/kubectl
RUN chmod +x kubectl

RUN mv kubectl /usr/local/bin/kubectl
ENTRYPOINT ["jenkins-slave"]