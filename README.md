# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

Name: Alan Samuel 
Reg.no: 212223040012

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
Server:
    
    import socket
    port = 60000
    s = socket.socket()
    host = socket.gethostname()
    s.bind((host, port))
    s.listen(5)
    print("Server listening on port", port)
    while True:
        conn, addr = s.accept()
        print('Connected to', addr)
        filename = 'received_file'
        with open(filename, 'rb') as f:
            l = f.read(1024)
            while l:
                conn.send(l)
                print('Sent', repr(l))
                l = f.read(1024)
        print('Done sending')
        ack = conn.recv(1024)
        print('Client acknowledgment:', ack.decode())
        conn.close()

Client:

    import socket
    s = socket.socket()
    host = socket.gethostname()
    port = 60000
    s.connect((host, port))
    s.send("Hello server!".encode())
    with open('received_file', 'wb') as f:
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
    

## OUPUT
![image](https://github.com/Alan-samuel/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147091803/5657ad17-292e-4e6d-92ea-b440bd8ce9e7)
![image](https://github.com/Alan-samuel/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/147091803/a0ee016b-5366-4049-8eb5-8526e24b83b2)


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
