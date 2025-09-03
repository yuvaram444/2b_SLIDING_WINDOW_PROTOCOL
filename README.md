# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## NAME : Yuvaram .S
## Reg.no : 212224230315
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
1.Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s

```
2.Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement recived from the server".encode())

```
## OUPUT
Client :

<img width="856" height="277" alt="Screenshot 2025-09-03 114237" src="https://github.com/user-attachments/assets/0a7f7154-0c36-4084-9ae3-c224094fa950" />

Server


<img width="841" height="214" alt="Screenshot 2025-09-03 114245" src="https://github.com/user-attachments/assets/fbf99c3a-8d81-4412-945b-83623c2b6a3f" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
