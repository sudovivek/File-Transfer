USING WGET -
------------------------------------------------------------------------------------------------------------------

**Download file from remote to local**
    
    wget http://10.10.10.10/demo.txt

**Download file and save to local location**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt

**Download file over HTTPS with certificate validation disabled**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt --no-check-certificate
------------------------------------------------------------------------------------------------------------------

</br>

USING CURL -
------------------------------------------------------------------------------------------------------------------

**Download file and display output**
    
    curl -v http://10.10.10.10/demo.txt

**Output save to file**
    
    curl -v http://10.10.10.10/demo.txt -o demo.txt

**Download file over HTTPS with certificate validation disabled**
    
    curl -v https://10.10.10.10/demo.txt -o demo.txt -k
------------------------------------------------------------------------------------------------------------------

</br>

NC / Ncat -
------------------------------------------------------------------------------------------------------------------

**Run listener on remote PC**
    
    nc64.exe -nlvp 443 > demo.txt

**Run client on local PC**
    
    nc -v 10.10.10.10 443 < demo.txt
------------------------------------------------------------------------------------------------------------------

</br>

SOCAT -
------------------------------------------------------------------------------------------------------------------

**Run listener on remote PC**
    
    socat TCP4-LISTEN:443,fork file:demo.txt

**Run client on local PC**
    
    socat TCP4:10.10.10.10:443 file:demo.txt,create
------------------------------------------------------------------------------------------------------------------

</br>

PHP -
------------------------------------------------------------------------------------------------------------------

**Run HTTP server on local PC**
    
    python -m http.server 80

    php -S 0.0.0.0:80

**Run PHP script on remote PC**
    
    echo "<?php file_put_contents('output.txt', fopen('http://10.10.10.10/demo.txt', 'r')); ?>" > demo.php && php demo.php

    php -r '$file = file_get_contents("https://10.10.10.10/demo.txt"); file_put_contents("demo.txt",$file);'
------------------------------------------------------------------------------------------------------------------

</br>

USING SSH - 
------------------------------------------------------------------------------------------------------------------

**SCP-**

**Copy file from local to remote**
    
    scp /tmp/demo.txt user@10.10.10.10:/tmp/

**Copy file from local to remote**

    scp demo.txt root@10.10.10.10:/root/

**Copy directory from local to remote**

    scp -r /tmp/demo/ user@10.10.10.10:/tmp/

**RSYNC-**

**Download web content to remote directory**
    
    rsync -av /tmp/demo/ root@10.10.10.10:/root/*

**Download web content to remote directory**

    rsync -av -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/

**Download web content to remote directory**

    rsync -av --port 22 -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/
