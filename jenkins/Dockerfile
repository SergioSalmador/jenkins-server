FROM jenkins/jenkins:lts

USER root

RUN apt-get update &&													\
    apt-get install -y python3 python-pip python3-pip nano wget

RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl &&												\
    mv ./kubectl /usr/local/bin

RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list && \
    apt-get install -y apt-transport-https ca-certificates gnupg &&							\
    curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add - && \
    apt-get -y update && apt-get -y install google-cloud-sdk 

RUN wget https://releases.hashicorp.com/terraform/0.12.26/terraform_0.12.26_linux_amd64.zip &&				\
    unzip terraform_0.12.26_linux_amd64.zip &&										\
    mv terraform /usr/local/bin/terraform
 
