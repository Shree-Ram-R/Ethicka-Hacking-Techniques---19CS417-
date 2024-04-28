# EXP.NO:1
# DATE:
# Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

# ALGORITHM:

### Step 1:

Design of echo server and client using python socket

### Step 2:

Implementation using Python code

### Step 3:

Testing the server and client 

## PROGRAM:
```python
import socket

HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()
    
    s.listen()
    print(f"Listening on {HOST}:{PORT}...")

    try:
        conn, addr = s.accept()
    except Exception as e:
        print(f"Error accepting connection: {e}")
        exit()

    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()


```
### Client Code:
```python
import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)

print(f"Received {data!r}")
```

## OUTPUT:
### Server side:
![server](https://github.com/Shree-Ram-R/Ethicka-Hacking-Techniques---19CS417-/assets/121288490/38fbfe0e-9163-4d8f-9280-57f9458b4a66)




### Client side:
![client](https://github.com/Shree-Ram-R/Ethicka-Hacking-Techniques---19CS417-/assets/121288490/83dd77b7-bdb5-40d9-a04d-00d5b1e0613a)

## Result:
The program is executed successfully
