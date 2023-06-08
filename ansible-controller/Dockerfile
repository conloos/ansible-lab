# Ubuntu Jammy
FROM ubuntu:jammy AS ubuntu-base
ENV DEBIAN_FRONTEND noninteractive
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# No Key Checking
ENV ANSIBLE_HOST_KEY_CHECKING False

# Install
RUN apt update -y 
RUN apt install -y openssh-server sudo python-is-python3 python3-pip iproute2

# Add User Ubuntu
RUN useradd -rm -d /home/ubuntu -s /bin/bash -G sudo ubuntu
RUN mkdir -p /etc/sudoers.d
RUN usermod -aG sudo ubuntu && echo "ubuntu ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
RUN chmod 0440 /etc/sudoers.d/ubuntu

# Specify ubuntu password
RUN echo "ubuntu:pass" | chpasswd

# Copy SSH Files
RUN mkdir -p /home/ubuntu/.ssh && \
    chown ubuntu:ubuntu /home/ubuntu/.ssh && \
    chmod 700 /home/ubuntu/.ssh
COPY --chown=ubuntu:ubuntu files/id_rsa /home/ubuntu/.ssh/id_rsa
COPY --chown=ubuntu:ubuntu files/id_rsa.pub /home/ubuntu/.ssh/id_rsa.pub
RUN chmod 600 /home/ubuntu/.ssh/id_rsa
RUN chmod 644 /home/ubuntu/.ssh/id_rsa.pub

# Bug fixing SSH
RUN sudo mkdir -p /run/sshd

# Expose port
EXPOSE 22

# Change Context
USER ubuntu:ubuntu
WORKDIR /home/ubuntu

# Prepare Dir for ansible Project
RUN mkdir -p /home/ubuntu/Workspace && \
    chown ubuntu:ubuntu /home/ubuntu/Workspace

# Start sshd
CMD ["/usr/bin/sudo", "/usr/sbin/sshd", "-D", "-o", "ListenAddress=0.0.0.0"]