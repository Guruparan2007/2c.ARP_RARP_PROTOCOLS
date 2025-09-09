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

```
NAME:GURUPARAN G
REG NO: 212224220030
```


## PROGRAM - ARP

CILENT:

```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
address = {"192.168.1.101":"68:34:21:81:97:82"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

SERVER:

```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

## OUPUT -ARP

<img width="435" height="171" alt="Screenshot 2025-09-10 015348" src="https://github.com/user-attachments/assets/ef9ff2a1-3a36-4d78-90a2-f2c249ce8cb7" />



## PROGRAM - RARP

CILENT:

````
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c, addr = s.accept()
address = {"68:34:21:81:97:82":"192.168.1.101"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
````

SERVER:

```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

## OUPUT - RARP

<img width="901" height="118" alt="Screenshot 2025-09-10 015407" src="https://github.com/user-attachments/assets/0964ac7d-f8ea-4862-809a-5f06437d1fff" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
