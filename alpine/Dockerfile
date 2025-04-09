FROM alpine:latest

RUN apk add --no-cache openssh nodejs npm python3

ARG SSH_USER
ARG SSH_PASSWORD

RUN adduser -D ${SSH_USER} && echo "${SSH_USER}:${SSH_PASSWORD}" | chpasswd

RUN ssh-keygen -A

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
