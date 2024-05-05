# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME : NITHIYANERANJAN S
## REGISTER NUMBER : 212223040136
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
## PROGRAM - ARP
### CLIENT
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"SA:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode()) 
    except KeyError:
        c.send("Not Found".encode())

```
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
### CLIENT OUTPUT
![image](https://github.com/NITHIYANERANJAN/2c.ARP_RARP_PROTOCOLS/assets/144979351/c2bdedc6-1493-4869-ada8-d37d9c27c45e)

### SERVER OUTPUT
![image](https://github.com/NITHIYANERANJAN/2c.ARP_RARP_PROTOCOLS/assets/144979351/966bf8f6-5c03-4735-9a68-ad332ba54ed3)


## PROGRAM - RARP
### CLIENT
```py
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
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
### CLIENT OUTPUT
![image](https://github.com/NITHIYANERANJAN/2c.ARP_RARP_PROTOCOLS/assets/144979351/ea01ce00-d801-4c00-8e0b-d7ed6f39744e)


### SERVER OUTPUT
![image](https://github.com/NITHIYANERANJAN/2c.ARP_RARP_PROTOCOLS/assets/144979351/387a35ec-6bd3-497e-a60e-8ae076c468fc)



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
