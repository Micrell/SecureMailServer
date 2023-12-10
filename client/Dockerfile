FROM ubuntu:latest

RUN apt-get update -y && apt-get upgrade -y

RUN apt-get install -y iputils-ping iproute2 dnsutils vim telnet

CMD ["tail", "-f", "/dev/null"]
