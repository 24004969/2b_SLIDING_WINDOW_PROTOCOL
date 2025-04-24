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
Developed by : Ajay J
Reg no : 212224110003
```
Client:
```

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("enter window size : "))
st= 0
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
Server :
```

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived".encode())
```


## OUPUT

![image](https://github.com/user-attachments/assets/374ecc64-7afc-4db0-8d03-5005102e86d2)


![image](https://github.com/user-attachments/assets/165a1e44-8fd9-4da3-bbec-e6e42501292f)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
