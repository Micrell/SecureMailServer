FROM ubuntu:latest

# Install service
RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install bind9 -y

# Install tools
RUN apt-get install -y iputils-ping iproute2 dnsutils vim

# By default /etc/bind/rndc.key is owned by bind but it most be owned by root to avoid
# open: /etc/bind/rndc.key: permission denied
RUN chown root:bind /etc/bind/rndc.key

COPY config/named /etc/default/named
COPY config/named.conf.local /etc/bind/named.conf.local
COPY config/db.pware.home /etc/bind/db.pware.home
COPY config/named.conf.options /etc/bind/named.conf.options

EXPOSE 53/tcp
EXPOSE 53/udp

CMD ["named", "-g"]



