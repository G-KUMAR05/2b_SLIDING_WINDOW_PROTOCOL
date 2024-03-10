# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
client:
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
server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```

## OUPUT
client:
![311495465-1a108bb7-2ecf-4dd5-922c-08e7974866e0](https://github.com/G-KUMAR05/2b_SLIDING_WINDOW_PROTOCOL/assets/133198953/58d4e736-4056-40d6-86ad-6a0f817f2ebe)
server:
![311495492-1e27bd97-142c-4889-bd4e-1444b7587998](https://github.com/G-KUMAR05/2b_SLIDING_WINDOW_PROTOCOL/assets/133198953/a592be8e-c85c-4b22-a9e1-a02fb7e0c1a8)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
