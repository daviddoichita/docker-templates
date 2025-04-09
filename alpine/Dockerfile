FROM alpine:latest

RUN apk add --no-cache openssh nodejs npm python3 curl vim doas

ARG SSH_USER
ARG SSH_PASSWORD
RUN adduser -D ${SSH_USER} && echo "${SSH_USER}:${SSH_PASSWORD}" | chpasswd
RUN ssh-keygen -A

RUN echo "permit persist :wheel" > /etc/doas.conf
RUN addgroup ${SSH_USER} wheel

RUN curl -L --output /usr/local/bin/gitlab-runner "https://s3.dualstack.us-east-1.amazonaws.com/gitlab-runner-downloads/latest/binaries/gitlab-runner-linux-amd64"
RUN chmod +x /usr/local/bin/gitlab-runner

RUN echo "192.168.0.238 gitlab.ddragos.com" >> /etc/hosts

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
