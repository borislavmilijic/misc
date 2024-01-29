# Use the Ubuntu Linux base image
FROM almalinux:latest
 
# Install required packages
RUN yum update -y \
yum install epel-release -y \
&& yum install jq -y \
&& yum install wget -y \
&& yum install unzip -y \
&& yum install vim -y
 
# Install AWS CLI version 2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
&& unzip awscliv2.zip \
&& ./aws/install \
&& rm -f awscliv2.zip \
&& rm -rf /aws*
 
 
# Install eksctl
RUN curl -sLO https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz \
&& tar xzf eksctl_$(uname -s)_amd64.tar.gz \
&& mv eksctl /usr/local/bin/eksctl \
&& rm -f eksctl_$(uname -s)_amd64.tar.gz
 
# # Copy crain
RUN curl -sLO https://github.com/google/go-containerregistry/releases/download/v0.16.1/go-containerregistry_Linux_x86_64.tar.gz \
&& mkdir /tmp/go-containerregistry \
&& tar xzf go-containerregistry_Linux_x86_64.tar.gz -C /tmp/go-containerregistry \
&& mv /tmp/go-containerregistry/crane /usr/local/bin/crane \
&& rm -rf /tmp/go-containerregistry \
&& rm -f go-containerregistry_Linux_x86_64.tar.gz
 
# Set the default command to run when the container starts
CMD ["/bin/bash"]