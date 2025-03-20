# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
To implement sliding window protocol using python sockets.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

Server.py
```
import socket
s=socket.socket()
s.bind(("localhost",8000))
s.listen(5)
c,add=s.accept()
size=int(input("Enter the number of frame to send: "))
l=list(range(size))
s=int(input("Enter the window size:  "))
st,i=0,0
n=s
while True:
    while (i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s

```
Client.py
```
import socket
s=socket.socket()
s.connect(("localhost",8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recieved from the server".encode())

```
## OUPUT
Server Side

![server](https://github.com/user-attachments/assets/2aa344b9-5052-49cb-89f8-2d3bfc8fc4c5)

Client Side

![client](https://github.com/user-attachments/assets/eb425e8a-3787-49e1-ab0a-8f254514a6a4)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
