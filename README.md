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
## CLIENT:
~~~
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addrr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~
## SERVER
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address :")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~


## OUPUT - ARP
<img width="942" height="526" alt="Screenshot 2026-05-19 135614" src="https://github.com/user-attachments/assets/d85a1d3c-9cae-4a31-a64a-356676f572c9" />
<img width="943" height="526" alt="Screenshot 2026-05-19 135700" src="https://github.com/user-attachments/assets/4bca517d-9e15-4709-aecd-18f52770aad6" />


## PROGRAM - RARP
## CLIENT
~~~
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
~~~
## SERVER
~~~
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address :")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
~~~

## OUPUT -RARP
<img width="950" height="528" alt="Screenshot 2026-05-19 142848" src="https://github.com/user-attachments/assets/7e657544-db58-46bc-a6e5-97cf3fac8e6d" />
<img width="945" height="533" alt="Screenshot 2026-05-19 143137" src="https://github.com/user-attachments/assets/f06f9c5a-84c2-4751-98ae-526ffd7a585c" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
