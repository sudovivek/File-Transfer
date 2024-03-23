USING WGET -
------------------------------------------------------------------------------------------------------------------

#### 

**Download file**
    
    wget http://10.10.10.10/demo.txt

**Output save to another location**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt

**If HTTPS Transfer**
    
    wget http://10.10.10.10/demo.txt -O /tmp/demo.txt --no-check-certificate
------------------------------------------------------------------------------------------------------------------

<br/>

USING CURL -
------------------------------------------------------------------------------------------------------------------

#### 

**Output show on screen**
    
    curl -v http://10.10.10.10/demo.txt

**Output save to file**
    
    curl -v http://10.10.10.10/demo.txt -o demo.txt

**-k to ingnore certificate**
    
    curl -v https://10.10.10.10/demo.txt -o demo.txt -k
------------------------------------------------------------------------------------------------------------------
