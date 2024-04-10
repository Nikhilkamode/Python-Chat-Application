# Python-Chat-Application
It is a simple project and contains two Python scripts server.py which handles client requests and client.py sends requests and receives responses from the server through socket communication.

Prerequisites
To run the Python script, your system must have the following programs/packages installed and the contact number should be saved in your phone (You can use the bulk contact number saving procedure of email). There is a way to save the contact number but cannot send the attachment.

Python 3.8

Approach
server.py needed to execute in the terminal.
client.py needed to execute from the client machine and enter the hostname or IP address.
the server will establish the connection between the server and the client through the socket.
now from the server or client text can be sent.

Server Code
# Program to accept client request
# Author @inforkgodara

import socket

s = socket.socket()
host = socket.gethostname()
print(' Server will start on host : ', host)
port = 8080
s.bind((host, port))
print()
print('Waiting for connection')
print()
s.listen(1)
conn, addr = s.accept()
print(addr, ' Has connected to the server')
print()
while 1:
    message = input(str('>> '))
    message = message.encode()
    conn.send(message)
    print('Sent')
    print()
    incoming_message = conn.recv(1024)
    incoming_message = incoming_message.decode()
    print(' Client : ', incoming_message)
    print()

    Client Code
    # Program to send request to the server
# Author @inforkgodara

import socket

s = socket.socket()
host = input(str('Enter hostname or host IP : '))
port = 8080
s.connect((host, port))
print('Connected to chat server')
while 1:
    incoming_message = s.recv(1024)
    incoming_message = incoming_message.decode()
    print(' Server : ', incoming_message)
    print()
    message = input(str('>> '))
    message = message.encode()
    s.send(message)
    print('Sent')
    print()
