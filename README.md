# 2c.SIMULATING ARP /RARP PROTOCOLS

## Developed By : SANJAY M
## Register No  : 212223230187

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
## Client.py:
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

## server.py:
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
## Client:
![Screenshot 2024-04-11 115905](https://github.com/sanjayofficial2005/2c.ARP_RARP_PROTOCOLS/assets/148048602/9356cf3f-ab4e-4fbd-8ad8-5400d323dfc9)
## Server:
![Screenshot 2024-04-11 115918](https://github.com/sanjayofficial2005/2c.ARP_RARP_PROTOCOLS/assets/148048602/ede3de38-2bdf-4180-ad66-bb96bdb33056)


## PROGRAM - RARP
## Client.py:
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
    c.send("Not Found".encode()
```

## server.py:
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
## Client:
![Screenshot 2024-04-11 120138](https://github.com/sanjayofficial2005/2c.ARP_RARP_PROTOCOLS/assets/148048602/d021d83c-2956-4575-b010-b407b4d9b02f)
## Server:
![Screenshot 2024-04-11 120149](https://github.com/sanjayofficial2005/2c.ARP_RARP_PROTOCOLS/assets/148048602/1fc19eb6-30a0-4f53-8b1e-8a0453cfd794)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
