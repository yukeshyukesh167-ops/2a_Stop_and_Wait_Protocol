# 2a_Stop_and_Wait_Protocol<img width="1482" height="222" alt="image" src="https://github.com/user-attachments/assets/53c4e999-ae92-4649-ba7f-9fb1d486b1d2" />

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
Server side

import socket
server_socket = socket.socket()
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
print("Server is waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to client:", addr)
while True:
    frame = conn.recv(1024).decode()
    if frame == "exit":
        print("Transmission completed.")
        break
    print("Received frame:", frame)
    ack = "ACK"
    conn.send(ack.encode())
conn.close()
server_socket.close()
Client side

import socket
import time
client_socket = socket.socket()
client_socket.connect(('localhost', 12345))
n = int(input("Enter number of frames to send: "))
for i in range(1, n + 1):
    frame = f"Frame {i}"
    print("Sending:", frame)
    client_socket.send(frame.encode())
    ack = client_socket.recv(1024).decode()
    print("Received:", ack)
    time.sleep(1)

client_socket.send("exit".encode())
client_socket.close()
## OUTPUT
<img width="1482" height="222" alt="image" src="https://github.com/user-attachments/assets/4424123c-1f1b-4502-830a-ad41b6450c35" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
