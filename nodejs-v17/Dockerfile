FROM node:17.7.2-alpine3.15
ARG USERNAME
ARG PASSWORD
ARG PROJECT_NAME
RUN apk add --update --no-cache openssh
RUN echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config
RUN adduser -h /home/$PROJECT_NAME -s /bin/sh -D $USERNAME
RUN echo -n "$USERNAME:$PASSWORD" | chpasswd
ENTRYPOINT ["/entrypoint.sh"]
EXPOSE 22
COPY entrypoint.sh /

WORKDIR "/home/$PROJECT_NAME"
RUN npm init -y
RUN touch index.js
