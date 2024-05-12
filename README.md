## EXP NO 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software : 
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program:
## Ping Command:
## Client:
```
import socket 
from pythonping import ping
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
while True:
    c, addr = s.accept()
    print("Connection from", addr)
    try:
        hostname = c.recv(1024).decode().strip()
        if hostname:
            try:
                response = str(ping(hostname, verbose=False))
                c.send(response.encode())
            except Exception as e:
                c.send("Ping failed: {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error:", e)
    finally:
        c.close()
```
## Server:
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
try:
    while True:
        ip = input("Enter the website you want to ping: ")
        s.send(ip.encode())
        response = s.recv(1024).decode()
        if response:
            print("Ping Result:", response)
        else:
            print("No response from server.")
except Exception as e:
    print("Error:", e)
finally:
    s.close()
```
## Trace Route Command:
```
from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```

## Output
## Ping Command:
## Client:

![image](https://github.com/sruthiviswanadham/4.Execution_of_NetworkCommends/assets/151760421/4b801c6b-c904-4085-9080-6db0fdf6753c)

## Server:

![image](https://github.com/sruthiviswanadham/4.Execution_of_NetworkCommends/assets/151760421/ce123219-15e3-4261-8e61-b6c554a302c9)

## Trace Route Command:

![image](https://github.com/sruthiviswanadham/4.Execution_of_NetworkCommends/assets/151760421/25af5a84-6eac-4a72-801b-eb3ddacc18a2)

## Result
Thus Execution of Network commands Performed 
