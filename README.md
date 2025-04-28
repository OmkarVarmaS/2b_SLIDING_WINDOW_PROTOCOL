# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## AIM:
To write python to implement the sliding window protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
   
## PROGRAM
CLIENT:
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
SERVER:
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT

CLIENT:
![Screenshot 2025-04-28 083427](https://github.com/user-attachments/assets/ee9e9197-dc5e-4d5f-a62a-7148842d00b5)

SERVER:
![Screenshot 2025-04-28 083451](https://github.com/user-attachments/assets/645bd206-f478-4192-b7a8-9a8cb7fcfe3f)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
