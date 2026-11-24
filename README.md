# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## NAME: M AADHAVAN NAGARAJAN
## REGISTER NUMBER: 212225040001
## AIM:
Python program to perform stop and wait protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
SERVER PROGRAM:
```

import socket
import ast

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)

print("Server waiting for client...")

c, addr = s.accept()

while True:
    data = c.recv(1024).decode()

    if not data:
        break

    frames = ast.literal_eval(data)
    print(frames)

    c.send("acknowledgement received from the server".encode())

c.close()
s.close()

```

CLIENT PROGRAM:
```

import socket

s = socket.socket()
s.connect(('localhost', 8001))

size = int(input("Enter number of frames to send : "))
l = list(range(size))

window = int(input("Enter Window Size : "))

i = 0

while i < len(l):
    frames = l[i:i + window]

    s.send(str(frames).encode())

    ack = s.recv(1024).decode()

    if ack:
        print(ack)
        i += window

s.close()

```
## OUPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2e71cb50-2554-44ac-a4f0-3fd07e17ab68" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/89a086c2-1a3b-4fde-83d4-8ec1ddc213d0" />

## RESULT
Thus python program to perform stop and wait protocol was successfully executed
