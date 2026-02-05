# File-Transfer-using-TCP-Sockets-
## AIM
To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:

1.Import the necessary python modules.

2.Create a socket connection using socket module.

3.Send the message to write into the file to the client file.

4.Open the file and then send it to the client in byte format.

5.In the client side receive the file from server and then write the content into it.
## PROGRAM
## SERVER
```
import socket

print("SERVER FILE STARTED")

port = 60000
s = socket.socket()
host = socket.gethostname()

s.bind((host, port))
s.listen(5)

print("Server is running...")
print("Waiting for client connection...")

while True:
    conn, addr = s.accept()
    print("Connected to:", addr)

    data = conn.recv(1024)
    print("Server received:", data.decode())

    with open("mytext.txt", "rb") as f:
        while True:
            chunk = f.read(1024)
            if not chunk:
                break
            conn.send(chunk)

    print("Done sending file")
    conn.send(b"\nThank you for connecting")
    conn.close()

```
## CLIENT
```
import socket

s = socket.socket()
host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('mytext.txt', 'wb') as f:
    while True:
        print('Receiving data...')
        data = s.recv(1024)
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('Connection closed')

```
## OUPUT
## SERVER
<img width="1053" height="416" alt="image" src="https://github.com/user-attachments/assets/466faf9a-0116-4b27-9105-4ebee753b15f" />

## CLIENT
<img width="1147" height="433" alt="image" src="https://github.com/user-attachments/assets/3a349dfc-92ee-4572-96d3-6885963d991b" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.

