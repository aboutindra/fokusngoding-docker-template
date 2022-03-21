FROM node:17.7.2-alpine3.15
ARG USERNAME
ARG PASSWORD
RUN apk add --update --no-cache openssh
RUN echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config
RUN adduser -h /home/$USERNAME -s /bin/sh -D $USERNAME
RUN echo -n $USERNAME':'$PASSWORD | chpasswd
ENTRYPOINT ["/entrypoint.sh"]
EXPOSE 22
COPY entrypoint.sh /
