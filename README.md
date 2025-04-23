# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
```
Name: RAJESHWARAN.D

Register number: 212223040165
```

## CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
   print('receiving data...')
   while True:
      data = s.recv(1024)
      print('data=%s', (data))
      if not data:
        break
      f.write(data)
print('Successfully get the file')
s.close()
print('connection closed')
```

## SERVER
```
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port)) 
s.listen(5) 
print("server listening on port",port)
while True:
  conn, addr = s.accept()
  print("Connected to",addr) 
  data = conn.recv(1024)
  print('Server received', repr(data))
  filename='mytext.txt'
  with open(filename,'rb') as f:
     l=f.read(1024)
     while l:
         conn.send(l)
         print('sent',repr(l))
         l=f.read(1024)
  print('Done sending')
  conn.send('Thank you for connecting'.encode())
  conn.close()
```
## OUTPUT
## CLIENT

<img width="828" alt="3cc" src="https://github.com/user-attachments/assets/727f9e61-f8ce-46bd-932e-742e84943cea">

## SERVER

<img width="828" alt="3cs" src="https://github.com/user-attachments/assets/a49c453a-0c61-4bf7-8474-5570b7efb3b3">

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
