---
aliases:
  - Connect to wifi linux
  - linux show wifi network
---
nmcli is a command-line tools which is used for controlling NetworkManager. *nmcli* command can also be used to display network device status, create, edit, activate/deactivate, and delete network connections.

### Syntax of nmcli
The nmcli command follows a specific syntax, enabling user to interact with Network Manager through the command line. The general syntax for nmcli is as follows:
```bash
nmcli [OPTIONS] OBJECTS {COMMAND | help}
```
Here,
- **OPTIONS:** Additional options that modify the behavior of nmcli.
- **OBJECTS:** Specifies the target of the operation (e.g., connections, device, etc.)
- **COMMAND:** Defines the action to be performed on the specified object.

# Implementation

#### (A) View Connections
```bash
nmcli connection show
```
This command lists all the available network connections on your system. It provides details such as the connections name, UUID, device, type, and status.
![](images/2024-01-11_17-00.png)

#### (B) Check Device Status
```bash
nmcli dev status
```
This command displays the current status of all network devices on your system. It shows whether each device is connected or disconnected, along with additional information like the device type and the connection type it is associated with. The output might vary with different machines.
![center](images/2024-01-11_17-03.png)

#### 

