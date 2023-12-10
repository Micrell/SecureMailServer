# SecureMailServer

# Docker compose

```sh
sudo docker compose up -d --build
```

# Check postfix config

Connect to postfix:

```sh
sudo docker exec -it postfix bash
```

In file `/etc/dovecot/conf.d/10-auth.conf` check that `disable_plaintext_auth` is set to `yes`and is uncommented.


# Add password for user bob and alice

Connect to postfix:

```sh
sudo docker exec -it postfix bash
```

Add passwords:

```sh
passwd bob # Enter password in stdin
passwd alice # Same
```

# Connect thunderbird

Do not forget to add bind9 DNS to your nameserver in `/etc/resolv.conf`add line `nameserver=172.20.0.9`
Then follow the thunderbird instruction to connect with POP3 port 110 and SMTP port 25.
You should be able to connect to alice and bob user with alice@pware.home and bob@pware.home with the passwords you previously set.



