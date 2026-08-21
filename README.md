# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### client.py
```python
import socket

s = socket.socket()
s.connect(('localhost', 8001))

n = int(input("Enter the number of frames: "))

for i in range(1, n + 1):
    data = input(f"Enter data for Frame {i}: ")

    print("Sending:", data)
    s.send(data.encode())

    ack = s.recv(1024).decode()
    print("Server:", ack)

s.close()
```
### server.py
```python
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(1)

print("Waiting for client...")
c, addr = s.accept()
print("Client connected")

while True:
    data = c.recv(1024).decode()

    if not data:
        break

    print("Received:", data)

    c.send("ACK".encode())

c.close()
s.close()
```
## OUTPUT

<img width="1742" height="1031" alt="image" src="https://github.com/user-attachments/assets/d465d124-836d-4b18-b62a-5b7dd54bb13b" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
