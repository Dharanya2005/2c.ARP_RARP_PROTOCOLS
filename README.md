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
# client:
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
# server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUTPUT - ARP
# client:
![Screenshot 2024-04-10 114311](https://github.com/Dharanya2005/2c.ARP_RARP_PROTOCOLS/assets/145742468/bb0c86c9-9c33-4ee0-9ecc-0737a954e63b)
# server:
![Screenshot 2024-04-10 114322](https://github.com/Dharanya2005/2c.ARP_RARP_PROTOCOLS/assets/145742468/4f0678d4-4d66-42e1-a907-28a82a9adbdf)


## PROGRAM - RARP
## client:
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
# server:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUTPUT -RARP
# client:
![Screenshot 2024-04-10 120956](https://github.com/Dharanya2005/2c.ARP_RARP_PROTOCOLS/assets/145742468/fd80f223-aa2c-4559-8dde-bdf70f365271)
# server:
![Screenshot 2024-04-10 121009](https://github.com/Dharanya2005/2c.ARP_RARP_PROTOCOLS/assets/145742468/22bc06c8-6a90-493a-8351-5646c7c97d9c)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
