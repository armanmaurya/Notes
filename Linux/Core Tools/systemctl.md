**Reboot System:-** 

```bash
systemctl reboot
```

**See service status:-**

```bash
systemctl list-units --type=service
```

## Management

---

**Start a Service:-**

```bash
systemctl start {servicename}
```

**Stop a Service:-**

```bash
systemctl stop {servicename}
```

**Restart a Service:-**

```bash
systemctl restart {servicename}
```

**Prevent service from starting:-**

```bash
systemctl mask {servicename}
```

**Enable a service:-**
Starting and Stopping a service only applies to the current runtime. What if you need to configure the service to start when the system boots ?

```bash
systemctl enable {servicename}
```

**Disable a service:-**
If you need to configure a service to not start when the system boots

```bash
systemctl disable {servicename}
```

**Confirm active status:-**
Confirms the current and startup status of specific services.

```bash
systemctl is-active {servicename}
```

**Confirm enable status:-**

```bash
systemctl is-enabled {servicename}
```

**Kill a service with signal 15:-**
Terminate services by using the kill subcommand. However, note that it's best to use the stop subcommand whenever possible. By default, this command sends signal 15, or SIGTERM 15, when sends a request to kill the system and enables the system to clean up as it does so.

```bash
systemctl kill {servicename}
```

**Kill a service with signal 9:-**
To force the system to kill a service immediately, admins can send signal 9 by typing the following command:

```bash
systemctl kill -s 9 {servicename}
```
