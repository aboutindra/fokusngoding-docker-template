FROM golang:1.18-alpine3.14
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
RUN go mod init $PROJECT_NAME
