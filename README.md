# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## Date: 12.02.2026
## Roll.no: 212225230084
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename='mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```

Client
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('mytext.txt', 'wb') as f:
 while True:
    print('receiving data...')
    data = s.recv(1024)
    print('data=%s', (data))
    if not data:
        break
    f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```


## OUPUT
Server
<img width="1164" height="274" alt="image" src="https://github.com/user-attachments/assets/b64e5c90-a3d7-4bfd-8778-3520723cdb91" />

Client
<img width="1158" height="304" alt="image" src="https://github.com/user-attachments/assets/ecb53f70-22c5-4b60-b520-c295c06667f9" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
