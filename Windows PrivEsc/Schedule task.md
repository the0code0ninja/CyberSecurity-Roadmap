# Schedule task

## Techniques for exploit Scheduled task:

1. Find scheduled task via **schtasks** command
2. Manual Enumeration 

### Technique 1: Find scheduled task via **schtasks** command

### Take RDP session of the target system

```bash
xfreerdp3 /u:user /p:password321 /cert:ignore /v:10.48.186.160 /dynamic-resolution
```

### Find scheduled task via **schtasks** command,

**/fo** ⇒ Format 

```
schtasks /fo LIST
```

here are lots of tasks from **\Microsoft\Windows** we don’t what those so we need to filter it more 

### Run this command for filter all the task by task names

**/I** ⇒ Ignore case 

```
schtasks /fo LIST | findstr /I taskname
```

### Now filter the list which not contain Microsoft

**/V**: Prints only lines that do not contain a match. 

```
schtasks /fo LIST | findstr /I taskname | findstr /I /V microsoft
```

Only one task we found 

### We try to find more info about this particular one task which we found before

**/tn** ⇒ Task name

**/v** ⇒ see detailed information 

```
schtasks /tn SaveCred /fo list /v
```

Here interesting thing we can see **Task To Run,** **Author** and **Schedule Type**

### Try to Open the file and read content inside

hear we can see the username and password in clear text

### Take access of a new shell via username and password we found previously

**runas** is a command like **sudo** in windows 

---

### Technique 2: Manual Enumeration

### Start enumerating from **C:\** drive manually

When I list all the C drive files and directory i can see hear a **DevTools** file which is pretty unusual  

### This is the file content of **CleanUp.ps1** file inside **DevTools**

---

## Three different for check file or folder permissions

### Tools we gonna use:

1. icacls
2. accesschk.exe
3. echo

## **Technique 1:**

### **icacls** command use to check the Files and Folder permissions

```
icacls [Directory / File Name]
```

**(M)** ⇒ Modify: **Read**, **Write**, **Execute** and **Delete** [ It can’t change any file permissions ]

**(F)** ⇒ Full: Read, Write, Execute and Delete  [ Full access can change file permissions also ]

**(I)** ⇒ Inherited

**(R)** ⇒ Read

**(X)** ⇒ Execute 

Directory permission is grater then file permission, mean if you have full permission on the directory and inside the file you have only read permission, but still you can do every thing not only read  

## Technique 2:

### Read the file permission using **accesschk.exe** this is an alternative tool of **icacls**

```
accesschk.exe -accepteula -q [filename]  #Show all the permissions 
accesschk.exe -accepteula -qu [username] [filename]   #Show permission only the courrent user
accesschk.exe -accepteula -quv [username] [filename]  #For more detailed output with verbosity
```

## Technique 3:

### Check file permission using **ECHO**

### We are echoing a file path which is not exist but if the execute automatically then the file will create

Now see the file created successfully test.txt

---

### So if we put a **reverseshell** payload inside this file then it give us a reverse shell

Pest the revershell payload on the RDP terminal 

### File auto execute and I got the revershell back
