# `Enumerating FTP - Port 21,21`

## --> For this, I have installed metaspliotable 2 linux, for FTP enumration
## Steps:- 
### 1) Get your target IP, and scan it through `Nmap tool ` - For tutorial go to [nmap](https://github.com/the0code0ninja/CyberSecurity-Roadmap/blob/main/02.%20Scanning%20%26%20Enumeration/NMAP.md)
<img width="577" height="183" alt="image" src="https://github.com/user-attachments/assets/60b40780-a072-4bb9-bee1-806b937e7593" />
<img width="1368" height="645" alt="image" src="https://github.com/user-attachments/assets/b87c0c50-3341-4945-8c6d-d86c96ba7126" />

Here , i got the `FTP` port opened, and i got the version as `vsftpd 2.3.4`

You can exploit this using `Metasploit Framework` or you can run some scripts of nmap, that can check for this open port
Running the default scripts, so we can get something... .. .

### EUREKA !!!, we have got that, `anonymous login` is accepted in the FTP server, so now, we can get into ftp with anonymous login
<img width="765" height="396" alt="image" src="https://github.com/user-attachments/assets/2d5e8e29-30a3-43cb-8b60-4058d11b77eb" />

### 2) Getting connected via FTP 
The command is `ftp <target_ip>` 
<img width="302" height="169" alt="image" src="https://github.com/user-attachments/assets/bf4865ed-27ee-4818-bb66-4b73fe3173b9" />
And now, i got connected to my target IP, and can get any file whichever i wanted .

### For `Metasploit Framework` Part, you can check to [Metasploit Framework](#)



