FROM ubuntu:24.04

RUN apt update && apt install -y openssh-server sudo
RUN useradd -ms /bin/bash ansible && \
    usermod -aG sudo ansible && \
    mkdir /var/run/sshd

RUN echo 'ansible ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

COPY --chown=ansible:ansible --chmod=600 ./authorized_keys /home/ansible/.ssh/authorized_keys

EXPOSE 80
EXPOSE 22

ENTRYPOINT ["/usr/sbin/sshd", "-D"]