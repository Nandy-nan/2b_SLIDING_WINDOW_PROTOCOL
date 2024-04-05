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
```
CLIENT:

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

SERVER:

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())


## OUPUT

CLIENT:


![Screenshot 2024-04-05 112839](https://github.com/Nandy-nan/2b_SLIDING_WINDOW_PROTOCOL/assets/153698914/ccfa7104-ac38-4a13-9552-895885e07795)

SERVER:

![Screenshot 2024-04-05 112849](https://github.com/Nandy-nan/2b_SLIDING_WINDOW_PROTOCOL/assets/153698914/1dea057c-c0e0-4639-9ab4-5e2e79b25277)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
