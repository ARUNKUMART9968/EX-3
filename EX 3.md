# IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

# EXP: 3

# DATE:22-03-2023

# AIM :
## To write a python program to perform sliding window protocol


# ALGORITHM :
## 1. Start the program.
## 2. Get the frame size from the user
## 3. To create the frame based on the user request.
## 4. To send frames to server from the client side.
## 5. If your frames reach the server it will send ACK signal to client otherwise it will sendNACK signal to client.

## 6. Stop the program

# CLIENT PROGRAM :
```PYTHON 3 

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window Size:"))
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
# SERVER PROGRAM :
```PYTHON 3
import socket![Uploading server2.png…]()

s=socket.socket()
s.connect(('localhost',8000))
while True:
	print(s.recv(1024).decode())
	s.send("acknowledgement recieved from the server".encode())
```


# SERVER OUTPUT :
![server2](https://github.com/ARUNKUMART9968/EX-3/assets/121215794/5a580906-37b4-4f66-bb8c-094d956fb396)
# CLIENT OUTPUT :
![2output](https://github.com/ARUNKUMART9968/EX-3/assets/121215794/ce69f406-5e13-43fd-b71b-9799554f9969)



# RESULT :
## Thus, python program to perform stop and wait protocol was successfully executed.
