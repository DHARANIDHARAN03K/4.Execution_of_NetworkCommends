# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
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
PROGRAM:
Ping Command
CLIENT:
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
        

        
        
        SERVER:
        
     ```   import socket
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
    
    TRACE ROUTE COMMAND

  ```  from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```
## Output

Ping Command:\n

CLIENT:

![image](https://github.com/DHARANIDHARAN03K/4.Execution_of_NetworkCommends/assets/144870858/e5ebdf62-e83c-4479-82f0-e732b3c9f927)
SERVER:\n
![image](https://github.com/DHARANIDHARAN03K/4.Execution_of_NetworkCommends/assets/144870858/49d69cb1-2549-456c-a9ee-517146dfe838)

Trace route command :\n
![image](https://github.com/DHARANIDHARAN03K/4.Execution_of_NetworkCommends/assets/144870858/f61b5dd2-c3a3-479d-98b7-99f24a0e9a33)




## Result
Thus Execution of Network commands Performed 
