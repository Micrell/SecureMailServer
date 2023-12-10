FROM ubuntu:latest

RUN useradd -m -s /bin/bash alice
RUN useradd -m -s /bin/bash bob

# Install service
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install postfix -y

# Install tools
RUN apt-get install -y iputils-ping iproute2 dnsutils vim

RUN echo "pware.home" > /etc/mailname
COPY config/main.cf /etc/postfix/main.cf

EXPOSE 25

RUN apt-get install -y dovecot-pop3d dovecot-imapd dovecot-core dovecot-antispam

RUN sed -i 's/\(disable_plaintext_auth = \)yes/\1no/' /etc/dovecot/conf.d/10-auth.conf

RUN service dovecot start

EXPOSE 110

CMD ["postfix", "start-fg"]

