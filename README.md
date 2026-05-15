# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP

server.py

```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

client.py

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="890" height="766" alt="Screenshot 2026-05-15 142040" src="https://github.com/user-attachments/assets/0bcd0436-bc0c-4a14-875a-ec0735ca4fc7" />


<img width="692" height="771" alt="Screenshot 2026-05-15 142208" src="https://github.com/user-attachments/assets/f0f2efcb-ed7d-4d86-85f6-03b040643b9c" />


## PROGRAM - RARP

server.py
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

client.py
```

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="750" height="668" alt="Screenshot 2026-05-15 143516" src="https://github.com/user-attachments/assets/b52bf9d8-4c3a-420b-b638-4bb193ef9645" />

<img width="701" height="760" alt="Screenshot 2026-05-15 143428" src="https://github.com/user-attachments/assets/c8660fb6-4fc0-476c-9811-7429a2eaf444" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
