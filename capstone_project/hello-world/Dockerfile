FROM node:16.13.1

RUN apt-get update  -y \
    && apt-get upgrade -y \
    && apt-get install -y \
    ssh \
    sshpass \
    sudo \
    software-properties-common

WORKDIR /home/hello-world

COPY ./hello-world/startup .

RUN useradd -rm -d /home/hello-world -s /bin/bash -g root -G sudo -u 1001 hello-world
RUN echo hello-world:12345 | chpasswd
RUN echo "hello-world ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

RUN mkdir -p /home/hello-world/.ssh

WORKDIR /app
COPY ./hello-world/app .
RUN npm install
RUN npm run test

CMD ["/bin/bash", "/home/hello-world/startup"]

