FROM ubuntu

RUN DEBIAN_FRONTEND="noninteractive"
RUN apt-get update \
 &&  apt-get install tzdata -y \
 && apt-get install openssh-server -y \
 && apt-get install openjdk-8-jdk -y \
 && apt-get install curl -y
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
RUN chmod +x ./kubectl && mv ./kubectl /usr/bin/kubectl
ADD ./k8s-config/deploy.yml ~/
RUN mkdir ~/.kube
ADD ./k8s-config/* ~/.kube

RUN mkdir /var/run/sshd
RUN echo 'root:redhat' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
CMD ["/usr/sbin/sshd", "-D" ]
EXPOSE 22
