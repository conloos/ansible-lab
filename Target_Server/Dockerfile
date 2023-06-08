# Ubuntu Jammy
FROM ubuntu:jammy
ENV DEBIAN_FRONTEND noninteractive
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install OpenSSH server with yum
RUN apt update -y 
RUN apt install -y openssh-server sudo

# Add User Ubuntu
RUN useradd -rm -d /home/ubuntu -s /bin/bash -G sudo ubuntu
RUN mkdir -p /etc/sudoers.d
RUN usermod -aG sudo ubuntu && echo "ubuntu ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
RUN chmod 0440 /etc/sudoers.d/ubuntu

# Allow login as root
RUN sed -ri 's/^#PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config

# Specify ubuntu password
RUN echo "ubuntu:pass" | chpasswd

# Add authorized
RUN mkdir -p /home/ubuntu/.ssh && \
    chown ubuntu:ubuntu /home/ubuntu/.ssh && \
    chmod 700 /home/ubuntu/.ssh
COPY --chown=ubuntu:ubuntu files/authorized_keys /home/ubuntu/.ssh/authorized_keys
RUN chmod 600 /home/ubuntu/.ssh/authorized_keys

# Bug fixing
RUN mkdir -p /var/run/sshd

# Expose port
EXPOSE 22

# Start sshd
CMD ["/usr/sbin/sshd", "-D"]