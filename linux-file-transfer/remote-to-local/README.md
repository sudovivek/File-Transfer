Command to start HTTP Server -
------------------------------------------------------------------------------------------------------------------

**Python HTTP Server**

    python2.7 -m SimpleHTTPServer 80
    python3 -m http.server 80

**PHP HTTP Server**

    php -S localhost:80

**Ruby HTTP Server**
    
    ruby -run -e httpd . -p 80
    
**BusyBox HTTP Server**

    busybox httpd -p 80
        
------------------------------------------------------------------------------------------------------------------
    
USING WGET -
------------------------------------------------------------------------------------------------------------------

**To initiate the HTTP server, execute the following command**

    python -m http.server 80

**On the Lcoal PC, run the following command after launching a python server on Remote PC**
    
    wget http://{REMOTE-IP}/demo.txt

**Utilize the -O flag to specify a different destination for the downloaded file**
    
    wget http://{REMOTE-IP}/demo.txt -O /tmp/demo.txt


**Utilize the -b flag to execute the process in the background**
    
    wget -b http://{REMOTE-IP}/demo.txt -O /tmp/demo.txt

**For downloading files over HTTPS with certificate validation disabled, use the following command**
    
    wget http://{REMOTE-IP}/demo.txt -O /tmp/demo.txt --no-check-certificate

**Execute this command on the Remote PC, while the python server is running on the Local PC**

    wget -O- --method=PUT --body-file=demo.txt http://{LOCAL-IP}/demo.txt

**Use the -i flag to fetch URLs from a file, where each URL is listed on a separate line**

    wget -i urls.txt

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

**Copy file from remote to local**
    
    scp /tmp/demo.txt user@10.10.10.10:/tmp/

**Copy file from remote to local**

    scp demo.txt root@10.10.10.10:/root/

**Copy directory from remote to local**

    scp -r /tmp/demo/ user@10.10.10.10:/tmp/

**RSYNC-**

**Download web content to local directory**
    
    rsync -av /tmp/demo/ root@10.10.10.10:/root/*

**Download web content to local directory**

    rsync -av -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/

**Download web content to local directory**

    rsync -av --port 22 -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/
