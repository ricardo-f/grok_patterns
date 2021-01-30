1. **Sudo commands execution**

```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} sudo(?:\\[%{POSINT:system.auth.pid}\\])?: \s*%{DATA:system.auth.user} :( %{DATA:system.auth.sudo.error} ;)? TTY=%{DATA:system.auth.sudo.tty} ; PWD=%{DATA:system.auth.sudo.pwd} ; USER=%{DATA:system.auth.sudo.user} ; COMMAND=%{GREEDYDATA:system.auth.sudo.command}
```

2. **SSH Access**

```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} sshd(?:\[%{NUMBER:system.auth.pid}\])?: %{DATA:system.auth.ssh.event} %{DATA:system.auth.ssh.method} for (invalid user )?%{DATA:system.auth.user} from %{IPORHOST:system.auth.ip} port %{NUMBER:system.auth.port} ssh2(: %{GREEDYDATA:system.auth.ssh.signature})?
```

3 . **Linux PAM audit:**

_Open Session:_
```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} %{DATA:system.auth.sudo.user} session opened for user %{USER:system.auth.sudo.user} by %{GREEDYDATA:system.auth.uid}
```
_Close Session_
```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} %{DATA:system.auth.sudo.user} session closed for user %{USER:system.auth.sudo.user}
```

4. **LINUX Useradd**

```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} useradd(?:\[%{POSINT:system.auth.pid}\])?: new user: name=%{DATA:system.auth.useradd.name}, UID=%{NUMBER:system.auth.useradd.uid}, GID=%{NUMBER:system.auth.useradd.gid}, home=%{DATA:system.auth.useradd.home}, shell=%{DATA:system.auth.useradd.shell}$
```

5. **LINUX GroupAdd**

```
%{SYSLOGTIMESTAMP:system.auth.timestamp} %{SYSLOGHOST:system.auth.hostname} useradd(?:\[%{POSINT:system.auth.pid}\])?: new user: name=%{DATA:system.auth.useradd.name}, UID=%{NUMBER:system.auth.useradd.uid}, GID=%{NUMBER:system.auth.useradd.gid}, home=%{DATA:system.auth.useradd.home}, shell=%{DATA:system.auth.useradd.shell}$
```
