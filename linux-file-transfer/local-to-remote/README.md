USING WGET -
------------------------------------------------------------------------------------------------------------------

**Download file**
    
    wget http://10.10.10.10/demo.txt

**Output save to another location**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt

**If HTTPS Transfer**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt --no-check-certificate
------------------------------------------------------------------------------------------------------------------

</br>

USING CURL -
------------------------------------------------------------------------------------------------------------------

**Output show on screen**
    
    curl -v http://10.10.10.10/demo.txt

**Output save to file**
    
    curl -v http://10.10.10.10/demo.txt -o demo.txt

**-k to ingnore certificate**
    
    curl -v https://10.10.10.10/demo.txt -o demo.txt -k
------------------------------------------------------------------------------------------------------------------

</br>

NC / Ncat -
------------------------------------------------------------------------------------------------------------------

**run on remote pc**
    
    nc64.exe -nlvp 443 > demo.txt

**run on local pc**
    
    nc -v 10.10.10.10 443 < demo.txt
------------------------------------------------------------------------------------------------------------------

</br>

SOCAT -
------------------------------------------------------------------------------------------------------------------

**run on local pc**
    
    socat TCP4-LISTEN:443,fork file:demo.txt

**run on remote pc**
    
    socat TCP4:10.10.10.10:443 file:demo.txt,create
------------------------------------------------------------------------------------------------------------------

</br>

PHP -
------------------------------------------------------------------------------------------------------------------

**run on local pc**
    
    python -m http.server 80

    php -S 0.0.0.0:80

**run on remote pc**
    
    echo "<?php file_put_contents('output.txt', fopen('http://10.10.10.10/demo.txt', 'r')); ?>" > demo.php && php demo.php

    php -r '$file = file_get_contents("https://10.10.10.10/demo.txt"); file_put_contents("demo.txt",$file);'
------------------------------------------------------------------------------------------------------------------

</br>

USING SSH - 
------------------------------------------------------------------------------------------------------------------

**SCP-**

**To Copy File**
    
    scp /tmp/demo.txt user@10.10.10.10:/tmp/

**To Copy File**

    scp demo.txt root@10.10.10.10:/root/

**To Copy Directory**

    scp -r /tmp/demo/ user@10.10.10.10:/tmp/

**RSYNC-**

**Web Content Download**
    
    rsync -av /tmp/demo/ root@10.10.10.10:/root/*

**Web Content Download**

    rsync -av -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/

**Web Content Download**

    rsync -av --port 22 -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/
